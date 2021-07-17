# Questions with Flair

This folder contains the artifacts and scripts from the investigation into open-ended vs. closed-end questions.  The idea is to identify open-ended questions from a text transcript.  Open-ended questions are a type of question that cannot be answered with a simple 'yes' or 'no' or with an otherwise static response.  The hypothesis is simply that a significant percentage of all open-ended questions can be classified as such based on the isolated text of the question itself, divorced from context.

Clearly conversational context will always be the ultimate determinant for classification of any question.  But as a start, using Flair, the results are promosing.

This investigation used the <a href="https://github.com/flairNLP/flair">FlairNLP</a> framework, along with a modified version of the TARS_6 dataset from the same framework.  An additional set of questions was taken from one of the Amazon Q/A files from data assembled by <a href="http://jmcauley.ucsd.edu/data/amazon/qa/">Julian McAuley of UCSD</a>.  

The final dataset was modified to reduce the types of questions to two basic categories: OPEN and CLOSED.  

All categories from the original TARS_6 dataset were collapsed into CLOSED with the exception of DESC which was relabelled as OPEN.  The Amazon dataset came with binary categories, making relabelling straightforward.

The final model used a training data set with 11500 training questions, with 4223 OPEN and 7227 CLOSED.  The test set had 500 questions, 138 OPEN and 362 CLOSED.

Results from 10 training epochs:

- F-score (micro) 0.97
- F-score (macro) 0.9636
- Accuracy 0.97

By class:

|                | precision | recall | f1-score | support |
|----------------|-----------|--------|----------|---------|
| open question  | 0.9020    | 1.0000 | 0.9485   | 138     |
| close question | 1.0000    | 0.9586 | 0.9788   | 362     |
|                |           |        |          |         |
| micro avg      | 0.9700    | 0.9700 | 0.9700   | 500     |
| macro avg      | 0.9510    | 0.9793 | 0.9736   | 500     |
| weighted avg   | 0.9729    | 0.9700 | 0.9705   | 500     |
| samples avg    | 0.9700    | 0.9700 | 0.9700   | 500     |
Although these results appear promising, the importance of conversational context cannot be overstated.  

