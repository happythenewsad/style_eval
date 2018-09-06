[Style Transfer in Text: Exploration and Evalution - Fu, et al.](https://arxiv.org/abs/1711.06861)
====

Short Summary
---

Paper addresses the problem of learning style transfer without the use of parallel corpora, using style embeddings (a previous work) and an auto-encoder model with multiple decoders. Attempts are made to improve evaluation metrics, but they do not appear to improve on human judgment and black-box classifiers. Example outputs from models are hard to visualize/express in a relatable way.

Objective
----
Conduct style transfer using non-parallel data. Main motivation is to avoid relying on rare and contrived parallel style corpora, like the Shakespeare old/new dataset.

Contributions
---------

- paper-news title dataset
- multi-decoder model
- style embedding model
- two evaluation metrics

Multi-decoder model
---------
An auto-encoder. Both encoder and decoder(s) are GRU RNNs.
Loss function appears to be a modified form of KL divergence, as standard for auto-encoders.

The system uses an adverserial loop to separate content representation from style representation. An external MLP is used for style prediction (styles are human-enumerated). This MLP lives outside the encoder-decoders loop. It's loss is passed to the auto-encoder as a parameter.
	
How the encoder can abstract content from its inputs is not elaborated, but references (Chen 2017).

There exists one decoder per style. The encoder learns content. 

The decoders work to ensure that the encoder does not contain style information. They do this by modifying input x to maximally confuse the classifier (maximizing style label entropy).


Style embedding model
---------------
Augmentation of first model, except with a single decoder.

Input vectors are a concatenation of style and content embeddings. Style embedding construction is not detailed; the author refers to (Li 2016).


Evaluation
---- 
- "Transfer strength" (aka style)
	- ill-defined. Defined as black box LSTM classifier that evaluates pairwise between styles
- "Content preservation"
	- cosine similarity between source and target embeddings

Results
---

System yielded a very good p-value from human evalaution (Mechanical Turk).


Comments
----

Example outputs from models are hard to visualize/express in a relatable way.

Like Hu, the multi-decoder model's adverserial components update separate parts of the latent structure z.

is the decoder effectively continuing the sequence received from the encoder?