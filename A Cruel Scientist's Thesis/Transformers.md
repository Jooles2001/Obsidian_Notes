2023-12-13
*Nicolas Béreux, Cyriaque Rousselot*
**Attention is All You Need**

# Original Transformer Architecture

## Tokenization
* An initial corpus of different words
	* Or take a n-gram

## Embedding
Goes from a one-hot encoding to a vector of large (but much smaller than the vocabulary size) dimension
==> Add the position of the word in the sentence in the embedding
$$\sin(\frac{k}{n^{2i/d}}) \quad\quad i \text{ is even} $$
$$\cos(\frac{k}{n^{2i/d}}) \quad\quad i \text{ is odd}$$
with $i$ the numerical position, $d$ the dimension of the word token, $n$ is by default 10_000, $k$ is the matrix dimension (after positional embedding)
--> into a key, query, value vector (divided arbitrarily)

## Encoder
From bottom to top
- Skip connection ==start==
- Layer Normalisation (not like Batch Norm, instead column by column)
- Attention Layer
- Skip connection ==end==
- ADD
- Skip connection ==start==
- Layer Normalisation
- Feedforward Network
- Skip connection ==end==

x6 Transformer Blocks in the paper

## Decoder
From bottom to top (iterate multiple times with a START token) 
*Skip connections follow the same pattern as the Encoder*
* START token with previous output of the decoder
* Layer Normalisation
* Self-Attention
* Queries into Encoder-Decoder Attention (output of the Encoder layer)
* Layer Norm
* Feedforward Net
* Loop here


# GPT-based models

**Example of NLP Task:** Stanford Question Answering Dataset

Autoregressive Generative Model

Radford, Alec, et al. 2018

### Byte Pair Encoding (BPE)
Compromise between the size of the sequences and vocabulary
Iteratively add the most frequent pair of "letters" to the new vocabulary
--> Most common n-grams and repeating patterns within words

### Unsupervised pre-training
$h_0 = U W_e + W_p$
$h_l = \texttt{transformer\_block}(h_{l-1})$
$P(u) = \texttt{softmax}(h_nW_e^T)$

https://bbycraft.net/llm

Models and datasets are getting bigger

## Beam Search
Anderson, Peter, et al 2016






