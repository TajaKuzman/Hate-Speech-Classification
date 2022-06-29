# Hate-Speech-Classification
 Experiments with binary classification of hate speech and its implicitness.

The spreadsheets (the original one from the Google Sheets - *Hate-Speech-Classification/data/Implicit hate speech.xlsx* and the ones that I prepared are located in the folder **data**).

First, I prepared the data into the format that is required for experiments with Transformers - see the code in *Hate-Speech-Classification/1-Data-Preparation.ipynb*. The following interventions were performed:
* Only comments are used, posts are discarded (as they are not annotated).
* "-*-*-*- " which indicates whether the comment is a reply to another comment was deleted from the comment text
* empty comments are discarded
* in the binary classification of hate speech (with two classes: acceptable and hate speech), instances that are annotated with both labels at once are discarded

The text length in no. of words (of the entire dataset, used for the two experiments):

| count | 5782.000000 |
|-------|-------------|
| mean  | 33.821861   |
| std   | 55.474635   |
| min   | 1.000000    |
| 25%   | 8.000000    |
| 50%   | 18.000000   |
| 75%   | 38.000000   |
| max   | 1387.000000 |

## Experiments

I performed 2 experiments:
* Experiment 1: binary classification of comments annotated for implicitness of hate speech. We have two classes: implicit hate speech (1) and explicit hate speech (0)
* Experiment 2: binary classification of hate speech. We have two classes: acceptable speech (0) and hate speech (1).

### Experiment 1: Implicitness

The statistics for the dataset:

|Label|Count|Perc|
|-----|-----|-----|
| Implicit | 329 |0.576|
| Explicit | 242 |0.424|
| Total | 571 |1|

### Experiment 2: Hate Speech

|Label|Count|Perc|
|-------------------|------|-----|
| Acceptable speech | 2864 |0.519|
| Hate speech       | 2652 |0.481|
| Total | 5516 |1|