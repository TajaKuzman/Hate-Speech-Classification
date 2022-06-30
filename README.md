# Hate-Speech-Classification
 Experiments with binary classification of hate speech and its implicitness.

The spreadsheets (the original one from the Google Sheets - *Hate-Speech-Classification/data/Implicit hate speech.xlsx* and the ones that I prepared) are located in the folder **data**.

First, I prepared the data into the format that is required for experiments with Transformers - see the code in *Hate-Speech-Classification/1-Data-Preparation.ipynb*. The following interventions were performed:
* Only comments are used, posts are discarded (as they are not annotated).
* `-*-*-*- ` which indicates whether the comment is a reply to another comment was deleted from the comment text
* empty comments are discarded
* in the binary classification of hate speech (with two classes: acceptable and hate speech), instances that are annotated with both labels at once are discarded

The text length in no. of words (of the entire dataset, used for the two experiments):

| count | 5771 |
|-------|-------------|
| mean  | 33.884422   |
| std   | 55.508957   |
| min   | 1.000000    |
| 25%   | 8.000000    |
| 50%   | 18.000000   |
| 75%   | 38.000000   |
| max   | 1387.000000 |

## Experiments

I performed 2 experiments:
* Experiment 1: binary classification of comments annotated for implicitness of hate speech. We have two classes: implicit hate speech (1) and explicit hate speech (0)
* Experiment 2: binary classification of hate speech. We have two classes: acceptable speech (0) and hate speech (1)

The code for the experiments is available on Kaggle:

* Experiment 1: https://www.kaggle.com/tajakuz/implicit-hate-speech-classification
* Experiment 2: 

### Experiment 1: Implicitness

The statistics for the dataset:

|Label|Count|Perc|
|-----|-----|-----|
| Implicit | 329 |0.576|
| Explicit | 242 |0.424|
| Total | 571 |1|

Results:

| model   |   microF1 |   macroF1 |   accuracy |
|:--------|----------:|----------:|-----------:|
| dummy   |  0.575581 |  0.365314 |      0.576 |
| BERT    |  0.651163 |  0.641667 |      0.651 |

We can see that BERT performs better than the baseline.

### Experiment 2: Hate Speech

|Label|Count|Perc|
|-------------------|------|-----|
| Acceptable speech | 2853 |0.518|
| Hate speech       | 2652 |0.482|
| Total | 5505 |1|