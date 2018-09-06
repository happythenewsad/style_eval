[Overview of the Author Obfuscation Task at PAN 2018: A New Approach to Measuring Safety](http://ceur-ws.org/Vol-2125/invited_paper_16.pdf)
======

Notes:
-----

Obfuscators should be:
- safe
- sound
- sensible

Unfortunately, the stylistic components "soundness" and "sensibleness" are scored by humans, so this paper does not directly inform style transfer evaluation.

Paper identifies a framework for evaluating obfuscators:
- assume a set of one-class author identifiers V
- for each document d_A, where A is the a priori author, credit an obfuscator O if it can successfully confuse a verifier (and by extension, a global collection of verifiers), causing the verifier to classify d_A as written by some author that is not A.


"Paradigmatically, there are still more or less
only two groups of obfuscation approaches: (1) the ones that are somewhat safe but
that produce rather unreadable text or text that is neither sound nor sensible, and (2) the
ones that produce sound and sensible texts but that are not really safe against authorship
verification."

Improvements in obfuscation require out-of-sentence contextual data.

Obfuscation and paraphrasing problems are closely related.

Automated style understanding is an open problem: "What is missing
are new and improved technologies for recognizing paraphrases, textual entailment,
grammaticality, and style deception—the existing technology is not mature enough to
easily replace manual inspection for evaluating soundness and sensibleness."