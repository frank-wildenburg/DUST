# DUST
**D**ataset of semantically **U**nderspecified **S**entences by **T**ype (DUST) as described and used in _Do Pre-Trained Language Models Detect and Understand Semantic Underspecification? _Ask the DUST!__

## Creation Context
This is the dataset used in our paper _Do Pre-Trained Language Models Detect and Understand Semantic Underspecification? _Ask the DUST!__. The authors of this paper are Frank Wildenburg, Michael Hanna and Sandro Pezzelle. The dataset contains sentence pairs of underspecified and more specified sentences, grouped by their type of underspecification. The sentences originate from other datasets containing ambiguity and underspecification, including [CLAIRE](https://github.com/acidann/claire), [LAVA](https://web.mit.edu/lavacorpus/) and [WSC](https://huggingface.co/datasets/winograd_wsc)

## Data
The dataset contains minimal pairs of sentences, where one sentence is _semantically underspecified_, and the other is not. The data is grouped by the type of semantic underspecification, as well as labeled with the phenomenon of underspecification it contains. These are:

* Type 1: Semantically and syntactically homogeneous expressions
  * Logical Form
  * Ellipsis
* Type 2: Semantically but not syntactically homogeneous expressions
  * PP attachment ambiguity
  * VP attachment ambiguity
  * Conjunction ambiguity
* Type 3: Syntactically but not semantically homogeneous expressions
  * Referential ambiguity
  * Added compounds
  * Fused heads
  * Implicit references
  * Metonymic references

## Data format
In the data of the sanity check, each row contains the perplexities of a sentence pair. These are contained in columns named ``{model} {order} perplexity``, where:
* The model can be one of ``GPT2`` (xl), ``FlanT5`` (xxl), ``OPT`` (13B), ``Mistral`` or ``Llama2-13b``
* The order is one of ``ppnn``, ``nnpp``, ``pnnp`` or ``nppn``

In the data of experiment 1, each row contains an ``underspecified sentence`` and a more specified ``control sentence``. For each of these sentences, we note its ``type`` of underspecification, the ``phenomenon`` the underspecified sentence contains, and the ``dataset`` it originates from. Then, the dataset contains the perplexities of these sentences for different variations of prompts, whose column name is ``{model} {prompt} {prompt order} perplexity``:
* The model can be ``GPT2-xl``, ``Flan-T5`` (xxl), ``Llama2`` (7B), ``OPT-13b``, or ``Mistral``
* The prompt can be ``under-over``, ``(un)ambigu``, ``little/lot detail``, or ``little/lot information``
* The prompt order can be one of ``uuoo``, ``oouu``, ``uoou`` or ``ouuo``.
For more detail on what these things mean, see our paper

In the data of experiment 2, each row contains an ``underspecified sentence``, two more specified control sentences ``control sentence 1`` and ``control sentence 2``, and two continuations ``continuation of control sentence 1`` and ``continuation of control sentence 2``. For each of these sentences, we note its ``type`` of underspecification and the ``phenomenon`` the underspecified sentence contains (the dataset is always "LAVA", so we do not note it). Then, the dataset contains the perplexities of these sentences for different variations of prompts, whose column name is ``{model} {reading} {prompt} {sentence}_{continuation}``:
* The model can be ``GPT2-xl``, ``Flan-T5 xxl``, ``Llama2-7b``, ``Llama2-13b``, ``OPT-13b``, or ``Mistral``
* The reading can be "" or ``counter``
* The prompt can be ``base``, ``thatis`` or ``more-likely``
* The sentence can be ``sen`` (underspecified sentence) or ``csen`` (control sentence)
* The continuation can be ``correct`` or ``incorrect``

## License
DUST is a non-commercial dataset which, like all of its component datasets, is intended for research purposes. We have also provided attribution to the creators of the component datasets, allowing it to be released in accordance with all of the licensing terms of these component datasets. Owing to the WikiHow data contained within, we also release DUST with a CC BY-NC-SA license.
