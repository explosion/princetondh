# Hi there


Welcome Digital Humanists! This is the repo where you can find
all code used for the the Priceton University online Workshop titled
"spaCy: A Python Library for Natural Language Processing" and held
Tue, Apr 4, 2023 4:30 PM – 6 PM EDT (GMT-4). Hope those of you who participated
had a good time and for the rest we hope you'll find this repository useful!


p.s.: We use [radicli](https://github.com/explosion/radicli) library for creating command line
interfaces, which we will be using in spaCy soon! Also, during the VSCode plugin for spaCy, which
is also coming soon!


## Notebooks

The [`notebooks`](notebooks) directory has three Jupyter notebooks:

1. [`intro_to_spacy.ipynb`](notebooks/intro_to_spacy.ipynb) is a short introduction to how to work with spaCy and a whirlwind tour of many of the tools spaCy provides.
2. [`casestudy_1.ipynb`](notebooks/casestudy_1.ipynb) walks through building a pipeline to extract information from restaurant reviews by identifying spans of interest such as mentions of cuisines or ratings. The pipeline is a blend of rule-based and learning-based techniques and there is an excersize to build your own rules.
3. [`casestudy_2.ipynb`](notebooks/casestudy_2.ipynb) focuses only on learned pipelines and the various tools spaCy provides to find spans in texts. It runs some parts of the [`litbank_pipeline`](litbank_pipeline) project.


## LitBank pipeline

The [LitBank dataset](https://github.com/dbamman/litbank/) is a collection of a 100 works of fiction
publicly available from Project Gutenberg majority of which were published between 1852 and 1911.
Each document is approximately the first 2000 words of the novels leading to a total of 
210532 tokens in the entire data set.

The [`litbank_pipeline`](litbank_pipeline) downloads LitBank and trains models on the Named Entity and Event
annotations. To learn about the entity annotations please checkout
[this paper](https://people.ischool.berkeley.edu/~dbamman/pubs/pdf/naacl2019_literary_entities.pdf) 
and [this one](https://aclanthology.org/P19-1353.pdf) for the event annotations.

Most config files in [`litbank_pipeline/configs`](litbank_pipeline/configs) project
were generated with an appropriate 
[`init config`](https://spacy.io/api/cli#init-config) command.  

The commands to preprocess are in 
[`litbank_pipeline/scripts/prepare.py`](litbank_pipeline/scripts/prepare.py). 
For the event trigger detection we wrote a special scoring function that computes the
precision, recall and F1 score only for the positive class i.e. the tokens that
have `EVENT` label. You can find the scorer in [`litbank_pipeline/scripts/positive_tagger_scorer.py`](litbank_pipeline/scripts/positive_tagger_scorer).



For the named entity recognition tasks there are config files to train
[`ner`](https://spacy.io/api/entityrecognizer), [`spancat` or `spancat_singlelabel`](https://spacy.io/api/spancategorizer) components with either the default 
[Convolutional Network](https://spacy.io/api/architectures#MaxoutWindowEncoder)
or a [Recurrent Network](https://spacy.io/api/architectures#TorchBiLSTMEncoder) encoder.

The `ner` component does only a single left-to-right pass over the document to find
all entities, while `spancat` classifies each possible span. This means that `ner` is
much more efficient than `spancat`, but `spancat` is more flexible. For a comparison between
the to checkout this [blogpost](https://explosion.ai/blog/spancat).


## Homework

As an excersize to get more familiar with spaCy we recommend training the different
architectures with the different encoders and see how they compare in terms of accuracy, speend
and the kinds of mistakes they make.  

We also think it would be a useful excersize to train a pipeline that has a single
`tok2vec` component providing representations both to a `tagger` component for the
event detection and a `ner` or `spancat` or `spancat_singlelabel` component for entity recognition.
To learn more about shared `tok2vec` layers please checkout: https://spacy.io/usage/embeddings-transformers#embedding-layers.


## References

- [An annotated dataset of literary entities](https://aclanthology.org/N19-1220) (Bamman et al., NAACL 2019)
- [Literary Event Detection](https://aclanthology.org/P19-1353) (Sims et al., ACL 2019)
