# Word Similarity and Analogy
:label:`sec_synonyms`
In :numref:`sec_word2vec_pretraining`, 
we trained a word2vec model on a small dataset, 
and applied it
to find semantically similar words 
for an input word.
In practice,
word vectors that are pretrained
on large corpora can be
applied to downstream
natural language processing tasks,
which will be covered later
in :numref:`chap_nlp_app`.
To demonstrate 
semantics of pretrained word vectors
from large corpora in a straightforward way,
let us apply them
in the word similarity and analogy tasks.
```{.python .input}
#@tab pytorch
from d2l import torch as d2l
import torch
from torch import nn
import os
```
## Loading Pretrained Word Vectors
Below lists pretrained GloVe embeddings of dimension 50, 100, and 300,
which can be downloaded from the [GloVe website](https://nlp.stanford.edu/projects/glove/).
The pretrained fastText embeddings are available in multiple languages.
Here we consider one English version (300-dimensional "wiki.en") that can be downloaded from the
[fastText website](https://fasttext.cc/).
To load these pretrained GloVe and fastText embeddings, we define the following `TokenEmbedding` class.
Below we load the
50-dimensional GloVe embeddings
(pretrained on a Wikipedia subset).
When creating the `TokenEmbedding` instance,
the specified embedding file has to be downloaded if it
was not yet.
Output the vocabulary size. The vocabulary contains 400000 words (tokens) and a special unknown token.
We can get the index of a word in the vocabulary, and vice versa.
## Applying Pretrained Word Vectors
Using the loaded GloVe vectors,
we will demonstrate their semantics
by applying them
in the following word similarity and analogy tasks.
### Word Similarity
Similar to :numref:`subsec_apply-word-embed`,
in order to find semantically similar words
for an input word
based on cosine similarities between
word vectors,
we implement the following `knn`
($k$-nearest neighbors) function.
```{.python .input}
#@tab pytorch
def knn(W, x, k):
    # Add 1e-9 for numerical stability
    cos = torch.mv(W, x.reshape(-1,)) / (
        torch.sqrt(torch.sum(W * W, axis=1) + 1e-9) *
        torch.sqrt((x * x).sum()))
    _, topk = torch.topk(cos, k=k)
    return topk, [cos[int(i)] for i in topk]
```
Then, we 
search for similar words
using the pretrained word vectors 
from the `TokenEmbedding` instance `embed`.
The vocabulary of the pretrained word vectors
in `glove_6b50d` contains 400000 words and a special unknown token. 
Excluding the input word and unknown token,
among this vocabulary
let us find 
three most semantically similar words
to word "chip".
Below outputs similar words
to "baby" and "beautiful".
### Word Analogy
Besides finding similar words,
we can also apply word vectors
to word analogy tasks.
For example,
“man”:“woman”::“son”:“daughter”
is the form of a word analogy:
“man” is to “woman” as “son” is to “daughter”.
Specifically,
the word analogy completion task
can be defined as:
for a word analogy 
$a : b :: c : d$, given the first three words $a$, $b$ and $c$, find $d$. 
Denote the vector of word $w$ by $\text{vec}(w)$. 
To complete the analogy,
we will find the word 
whose vector is most similar
to the result of $\text{vec}(c)+\text{vec}(b)-\text{vec}(a)$.
Let us verify the "male-female" analogy using the loaded word vectors.
Below completes a
“capital-country” analogy: 
“beijing”:“china”::“tokyo”:“japan”.
This demonstrates 
semantics in the pretrained word vectors.
For the
“adjective-superlative adjective” analogy
such as 
“bad”:“worst”::“big”:“biggest”,
we can see that the pretrained word vectors
may capture the syntactic information.
To show the captured notion
of past tense in the pretrained word vectors,
we can test the syntax using the
"present tense-past tense" analogy: “do”:“did”::“go”:“went”.
## Summary
* In practice, word vectors that are pretrained on large corpora can be applied to downstream natural language processing tasks.
* Pretrained word vectors can be applied to the word similarity and analogy tasks.
## Exercises
1. Test the fastText results using `TokenEmbedding('wiki.en')`.
1. When the vocabulary is extremely large, how can we find similar words or complete a word analogy faster?
:begin_tab:`mxnet`
[Discussions](https://discuss.d2l.ai/t/387)
:end_tab:
:begin_tab:`pytorch`
[Discussions](https://discuss.d2l.ai/t/1336)
:end_tab: