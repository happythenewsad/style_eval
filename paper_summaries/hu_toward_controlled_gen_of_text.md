[Toward Controlled Generation of Text - Hu, et al.](https://arxiv.org/abs/1703.00955)
=================================================

Short Summary
---

Paper seeks to generate realistic (English) sentences using a VAE in a wake-sleep configuration. Semantic and stylistic signals can be injected to coerce specific meaning and styles.

Objective
----------
Generate plausible sentences conditioned on sentiment variables.

Model
------

A VAE enhanced with an extended wake-sleep procedure. 

The whole setup consists of VAE components "Encoder" and "Generator", plus an array of Discriminators that are fed by the VAE output and feed back in the VAE's structured latent state "c". The VAE's latent state differs from a vanilla AE in that it is composed of two segments, "z|c". Discriminators are only allowed to update "c", and the VAE is constrained to only update "z" during training. The result is that stylistic state "c" is independent from "z".

Discriminators
---------------
These are style-specific, and each is responsible for a region of "c". They are bootstrapped with labeled training data, then are improved during the wake-sleep coordination with the VAE until convergence.


Generator
----------
LSTM-RNN, with softmax. The c subvector can contain both continuous and discrete variables (sentiment categories, etc).


Evaluation
----------
Metric: label accuracy.
Method: External sentiment clasifiers.

Results
--------
Outperforms stated previous work: a semi-supervised VAE (Kingma 2014).
Reaches about 83% sentiment classificiation accuracy, although performance varies greatly with datasets used.

Comments
--------
I would like to know more detail about how the "c" stylistic state is kept independent from the VAE's "z" latent state. I suspect that further reading into VAEs and wake-sleep systems will improve my understanding.

It is noted that the undifferentiability of text input is mitigated by
continuous approximation using softmax with decreasing temperature.