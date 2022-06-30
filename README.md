# Hate-Speech-Classification
 Experiments with binary classification of hate speech and its implicitness.

The spreadsheets (the original one from the Google Sheets - *Hate-Speech-Classification/data/Implicit hate speech.xlsx* and the ones that I prepared) are located in the folder **data**.

First, I prepared the data into the format that is required for experiments with Transformers - see the code in *Hate-Speech-Classification/1-Data-Preparation.ipynb*. The following interventions were performed:
* Only comments are used, posts are discarded (as they are not annotated).
* `-*-*-*- ` which indicates whether the comment is a reply to another comment was deleted from the comment text
* empty comments are discarded
* duplicated comments are discarded
* in the binary classification of hate speech (with two classes: acceptable and hate speech), instances that are annotated with both labels at once are discarded

The text length in no. of words (of the entire dataset, used for the two experiments):


| count |     5706      |
|-----|-----|
| mean  |       34.0135 |
| std   |       55.6401 |
| min   |        1      |
| 25%   |        8      |
| 50%   |       18      |
| 75%   |       38      |
| max   |     1387      |

## Experiments

I performed 2 experiments:
* Experiment 1: binary classification of comments annotated for implicitness of hate speech. We have two classes: implicit hate speech (1) and explicit hate speech (0)
* Experiment 2: binary classification of hate speech. We have two classes: acceptable speech (0) and hate speech (1)

The code for the experiments is available on Kaggle:

* Experiment 1: https://www.kaggle.com/tajakuz/implicit-hate-speech-classification
* Experiment 2: https://www.kaggle.com/code/tajakuz/hate-speech-binary-classification

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
| BERT    |  0.645349 |  0.633442 |      0.645 |

We can see that BERT performs better than the baseline.

I experimented with different numbers of epochs and the results revealed the optimum number is 60.

### Experiment 2: Hate Speech

|Label|Count|Perc|
|:------------------|---------------------:|---------------------:|
| Acceptable speech |                 2821 |0.519|
| Hate speech       |                 2619 |0.481|
| Total | 5440 |1|

Results:

| model   |   microF1 |   macroF1 |   accuracy |
|:--------|----------:|----------:|-----------:|
| dummy   |  0.518382 |  0.341404 |      0.518 |
| BERT    |  0.765319 |  0.765304 |      0.765 |

The Transformer model outperforms the baseline for 15 points (in micro F1), which is significant.

The results show that these experiments gave better results than prediction of implicitness. However, here, the model was trained on 10x more instances. The experimentation with different numbers of epochs revealed that training the model for 20 epochs gives the best results.