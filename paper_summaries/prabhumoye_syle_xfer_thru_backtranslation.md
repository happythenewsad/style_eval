[Style Transfer Through Back-Translation - Prabhumoye](https://arxiv.org/abs/1804.09000)
====

Short Summary
---

The proposed model creates a style-agnostic representation of an English input sentence using A->B then B->A neural machine translators, with the objective of style transfer with minimal semantic drift. A style-specific transformation step adds specific style to the style-agnostic representation.

Objective
----
Textual style transfer while minimizing semantic drift.


The author's main hypothesis is that translation to and from an intermediate language, via pre-existing, reasonably accurate machine translators, will abstract the content of a text while discarding style.

Model
-----

(MT w/ encoder, decoder) -> (MT' with encoder) -> latent state z -> [style decoders] -> [styled text] -> classifier -> predicted label

Machine translators MT and MT' are inverses of each other, except that the output of MT' is not a first-language sentence, but rather a latent state z."z" is passed to a bank of style decoders (1 per style) to be decoded into respective styles.

The style decoders are trained separately from the machine translators.

The (single) style classifier is a supervised CNN. The objective function is a class-wise log likelihoood function. A heuristic is used to improve performance: input is preprocessed using style-specific lexicons. 1-hot features are added to word embeddings if a word is identified with a particular style.

The classifier's prediction is fed back into the style decoder bank. This allows style encoders to learn to generate text in their respective styles.


Evaluation
-----
Metrics: style transfer accuracy, preservation of meaning, fluency.

The first is evaluated by the classifier. The latter two are evaluated by humans.

Comments
-----

Content abstraction happens because  the machine translators are trained on a style-agnostic corpus. It would seem that the availability, size, and usefulness of such corpora are essential for this model.

Softmax is used on style decoder output to make the discrete tokens differentiable, similar to Hu.

This paper confirms that BLEU and ROUGE metrics are not suitable for capturing meaning.

It would be great if there existed a visualization for how the generative style decoders learn style from the classifier's loss signal. For now, this process is not intuitive for me.