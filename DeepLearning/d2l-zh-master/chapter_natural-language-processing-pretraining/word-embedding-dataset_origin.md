# The Dataset for Pretraining Word Embeddings
:label:`sec_word2vec_data`
Now that we know the technical details of 
the word2vec models and approximate training methods,
let us walk through their implementations. 
Specifically,
we will take the skip-gram model in :numref:`sec_word2vec`
and negative sampling in :numref:`sec_approx_train`
as an example.
In this section,
we begin with the dataset
for pretraining the word embedding model:
the original format of the data
will be transformed
into minibatches
that can be iterated over during training.
```{.python .input}
#@tab pytorch
from d2l import torch as d2l
import math
import torch
import os
import random
```
## Reading the Dataset
The dataset that we use here
is [Penn Tree Bank (PTB)]( https://catalog.ldc.upenn.edu/LDC99T42). 
This corpus is sampled
from Wall Street Journal articles,
split into training, validation, and test sets.
In the original format,
each line of the text file
represents a sentence of words that are separated by spaces.
Here we treat each word as a token.
After reading the training set,
we build a vocabulary for the corpus,
where any word that appears 
less than 10 times is replaced by 
the "&lt;unk&gt;" token.
Note that the original dataset
also contains "&lt;unk&gt;" tokens that represent rare (unknown) words.
## Subsampling
Text data
typically have high-frequency words
such as "the", "a", and "in":
they may even occur billions of times in
very large corpora.
However,
these words often co-occur
with many different words in
context windows, providing little useful signals.
For instance,
consider the word "chip" in a context window:
intuitively
its co-occurrence with a low-frequency word "intel"
is more useful in training
than 
the co-occurrence with a high-frequency word "a".
Moreover, training with vast amounts of (high-frequency) words
is slow.
Thus, when training word embedding models, 
high-frequency words can be *subsampled* :cite:`Mikolov.Sutskever.Chen.ea.2013`.
Specifically, 
each indexed word $w_i$ 
in the dataset will be discarded with probability
$$ P(w_i) = \max\left(1 - \sqrt{\frac{t}{f(w_i)}}, 0\right),$$
where $f(w_i)$ is the ratio of 
the number of words $w_i$
to the total number of words in the dataset, 
and the constant $t$ is a hyperparameter
($10^{-4}$ in the experiment). 
We can see that only when
the relative frequency
$f(w_i) > t$  can the (high-frequency) word $w_i$ be discarded, 
and the higher the relative frequency of the word, 
the greater the probability of being discarded.
The following code snippet 
plots the histogram of
the number of tokens per sentence
before and after subsampling.
As expected, 
subsampling significantly shortens sentences
by dropping high-frequency words,
which will lead to training speedup.
For individual tokens, the sampling rate of the high-frequency word "the" is less than 1/20.
In contrast, 
low-frequency words "join" are completely kept.
After subsampling, we map tokens to their indices for the corpus.
## Extracting Center Words and Context Words
The following `get_centers_and_contexts`
function extracts all the 
center words and their context words
from `corpus`.
It uniformly samples an integer between 1 and `max_window_size`
at random as the context window size.
For any center word,
those words 
whose distance from it
does not exceed the sampled
context window size
are its context words.
Next, we create an artificial dataset containing two sentences of 7 and 3 words, respectively. 
Let the maximum context window size be 2 
and print all the center words and their context words.
When training on the PTB dataset,
we set the maximum context window size to 5. 
The following extracts all the center words and their context words in the dataset.
## Negative Sampling
We use negative sampling for approximate training. 
To sample noise words according to 
a predefined distribution,
we define the following `RandomGenerator` class,
where the (possibly unnormalized) sampling distribution is passed
via the argument `sampling_weights`.
For example, 
we can draw 10 random variables $X$
among indices 1, 2, and 3
with sampling probabilities $P(X=1)=2/9, P(X=2)=3/9$, and $P(X=3)=4/9$ as follows.
For a pair of center word and context word, 
we randomly sample `K` (5 in the experiment) noise words. According to the suggestions in the word2vec paper,
the sampling probability $P(w)$ of 
a noise word $w$
is 
set to its relative frequency 
in the dictionary
raised to 
the power of 0.75 :cite:`Mikolov.Sutskever.Chen.ea.2013`.
## Loading Training Examples in Minibatches
:label:`subsec_word2vec-minibatch-loading`
After
all the center words
together with their
context words and sampled noise words are extracted,
they will be transformed into 
minibatches of examples
that can be iteratively loaded
during training.
In a minibatch,
the $i^\mathrm{th}$ example includes a center word
and its $n_i$ context words and $m_i$ noise words. 
Due to varying context window sizes,
$n_i+m_i$ varies for different $i$.
Thus,
for each example
we concatenate its context words and noise words in 
the `contexts_negatives` variable,
and pad zeros until the concatenation length
reaches $\max_i n_i+m_i$ (`max_len`).
To exclude paddings
in the calculation of the loss,
we define a mask variable `masks`.
There is a one-to-one correspondence
between elements in `masks` and elements in `contexts_negatives`,
where zeros (otherwise ones) in `masks` correspond to paddings in `contexts_negatives`.
To distinguish between positive and negative examples,
we separate context words from noise words in  `contexts_negatives` via a `labels` variable. 
Similar to `masks`,
there is also a one-to-one correspondence
between elements in `labels` and elements in `contexts_negatives`,
where ones (otherwise zeros) in `labels` correspond to context words (positive examples) in `contexts_negatives`.
The above idea is implemented in the following `batchify` function.
Its input `data` is a list with length
equal to the batch size,
where each element is an example
consisting of
the center word `center`, its context words `context`, and its noise words `negative`.
This function returns 
a minibatch that can be loaded for calculations 
during training,
such as including the mask variable.
Let us test this function using a minibatch of two examples.
## Putting All Things Together
Last, we define the `load_data_ptb` function that reads the PTB dataset and returns the data iterator and the vocabulary.
```{.python .input}
#@tab pytorch
#@save
def load_data_ptb(batch_size, max_window_size, num_noise_words):
    """Download the PTB dataset and then load it into memory."""
    num_workers = d2l.get_dataloader_workers()
    sentences = read_ptb()
    vocab = d2l.Vocab(sentences, min_freq=10)
    subsampled, counter = subsample(sentences, vocab)
    corpus = [vocab[line] for line in subsampled]
    all_centers, all_contexts = get_centers_and_contexts(
        corpus, max_window_size)
    all_negatives = get_negatives(
        all_contexts, vocab, counter, num_noise_words)
    class PTBDataset(torch.utils.data.Dataset):
        def __init__(self, centers, contexts, negatives):
            assert len(centers) == len(contexts) == len(negatives)
            self.centers = centers
            self.contexts = contexts
            self.negatives = negatives
        def __getitem__(self, index):
            return (self.centers[index], self.contexts[index],
                    self.negatives[index])
        def __len__(self):
            return len(self.centers)
    dataset = PTBDataset(all_centers, all_contexts, all_negatives)
    data_iter = torch.utils.data.DataLoader(dataset, batch_size, shuffle=True,
                                      collate_fn=batchify,
                                      num_workers=num_workers)
    return data_iter, vocab
```
Let us print the first minibatch of the data iterator.
## Summary
* High-frequency words may not be so useful in training. We can subsample them for speedup in training.
* For computational efficiency, we load examples in minibatches. We can define other variables to distinguish paddings from non-paddings, and positive examples from negative ones.
## Exercises
1. How does the running time of code in this section changes if not using subsampling?
1. The `RandomGenerator` class caches `k` random sampling results. Set `k` to other values and see how it affects the data loading speed.
1. What other hyperparameters in the code of this section may affect the data loading speed?
:begin_tab:`mxnet`
[Discussions](https://discuss.d2l.ai/t/383)
:end_tab:
:begin_tab:`pytorch`
[Discussions](https://discuss.d2l.ai/t/1330)
:end_tab: