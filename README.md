# Hi there


Welcome Digital Humanists! This is the repo where you can find
all code used for the the Priceton University online Workshop titled
"spaCy: A Python Library for Natural Language Processing" and held
Tue, Apr 4, 2023 4:30 PM – 6 PM EDT (GMT-4). Hope those of you who participated
had a good time and for the rest we hope you'll find this repository useful!

## Notebooks

The [`notebooks`](notebooks) directory has three Jupyter notebooks:

1. `intro_to_spacy.ipynb` is a short introduction to how to work with spaCy and a whirlwind tour of many of the tools spaCy provides.
2. `casestudy_1.ipynb` walks through building a pipeline to extract information from restaurant reviews by identifying spans of interest such as mentions of cuisines or ratings. The pipeline is a blend of rule-based and learning-based techniques and there is an excersize to build your own rules.
3. `casestudy_2.ipynb` focuses only on learned pipelines and the various tools spaCy provides to find spans in texts. It runs some parts of the `litbank_pipeline` project.


## LitBank pipeline

The [LitBank dataset](https://github.com/dbamman/litbank/) is a collection of a 100 works of fiction
publicly available from Project Gutenberg majority of which were published between 1852 and 1911.
Each document is approximately the first 2000 words of the novels leading to a total of 
210532 tokens in the entire data set.

The `litbank_pipeline` downloads LitBank and trains models on the Named Entity and Event
annotations. To learn about the entity annotations please checkout
[this paper](https://people.ischool.berkeley.edu/~dbamman/pubs/pdf/naacl2019_literary_entities.pdf) 
and [this one](https://aclanthology.org/P19-1353.pdf) for the event annotations.

All config files in `litbank_pipeline/configs` project were generated with an appropriate 
[`init config`](https://spacy.io/api/cli#init-config) command.
