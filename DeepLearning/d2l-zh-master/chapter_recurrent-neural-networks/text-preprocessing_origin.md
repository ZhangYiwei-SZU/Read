# Text Preprocessing
:label:`sec_text_preprocessing`
We have reviewed and evaluated
statistical tools 
and prediction challenges
for sequence data.
Such data can take many forms.
Specifically,
as we will focus on
in many chapters of the book,
text is one of the most popular examples of sequence data.
For example,
an article can be simply viewed as a sequence of words, or even a sequence of characters.
To facilitate our future experiments
with sequence data,
we will dedicate this section
to explain common preprocessing steps for text.
Usually, these steps are:
1. Load text as strings into memory.
1. Split strings into tokens (e.g., words and characters).
1. Build a table of vocabulary to map the split tokens to numerical indices.
1. Convert text into sequences of numerical indices so they can be manipulated by models easily.
```{.python .input}
#@tab pytorch
import collections
from d2l import torch as d2l
import re
```
## Reading the Dataset
To get started we load text from H. G. Wells' [*The Time Machine*](http://www.gutenberg.org/ebooks/35).
This is a fairly small corpus of just over 30000 words, but for the purpose of what we want to illustrate this is just fine.
More realistic document collections contain many billions of words.
The following function reads the dataset into a list of text lines, where each line is a string.
For simplicity, here we ignore punctuation and capitalization.
## Tokenization
The following `tokenize` function
takes a list (`lines`) as the input,
where each list is a text sequence (e.g., a text line).
Each text sequence is split into a list of tokens.
A *token* is the basic unit in text.
In the end,
a list of token lists are returned,
where each token is a string.
## Vocabulary
The string type of the token is inconvenient to be used by models, which take numerical inputs.
Now let us build a dictionary, often called *vocabulary* as well, to map string tokens into numerical indices starting from 0.
To do so, we first count the unique tokens in all the documents from the training set,
namely a *corpus*,
and then assign a numerical index to each unique token according to its frequency.
Rarely appeared tokens are often removed to reduce the complexity.
Any token that does not exist in the corpus or has been removed is mapped into a special unknown token “&lt;unk&gt;”.
We optionally add a list of reserved tokens, such as
“&lt;pad&gt;” for padding,
“&lt;bos&gt;” to present the beginning for a sequence, and “&lt;eos&gt;” for the end of a sequence.
We construct a vocabulary using the time machine dataset as the corpus. 
Then we print the first few frequent tokens with their indices.
Now we can convert each text line into a list of numerical indices.
## Putting All Things Together
Using the above functions, we package everything into the `load_corpus_time_machine` function, which returns `corpus`, a list of token indices, and `vocab`, the vocabulary of the time machine corpus.
The modifications we did here are:
i) we tokenize text into characters, not words, to simplify the training in later sections;
ii) `corpus` is a single list, not a list of token lists, since each text line in the time machine dataset is not necessarily a sentence or a paragraph.
## Summary
* Text is an important form of sequence data.
* To preprocess text, we usually split text into tokens, build a vocabulary to map token strings into numerical indices, and convert text data into token indices for  models to manipulate.
## Exercises
1. Tokenization is a key preprocessing step. It varies for different languages. Try to find another three commonly used methods to tokenize text.
1. In the experiment of this section, tokenize text into words and vary the `min_freq` arguments of the `Vocab` instance. How does this affect the vocabulary size? 
[Discussions](https://discuss.d2l.ai/t/115)