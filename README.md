# Common-Sense-Validation-Task-Online-Competition-With-concepts-of-Artificial-Intelligence-and-NLP

In this prooject, I presented the language model system submitted to SemEval-2020 Task 4 competition:
“Commonsense Validation & Explanation.” I participated in one one subtask for subtask A: validation. I
implemented with transfer learning using the pre-trained language model “BERT”. The ensemble model
solves this problem, making the model accuracy reached to 96.52% on subtaskA, which just worse than
human’s by only 3% accuracy.

# Introduction
The task is to evaluate how well model can sense English dataset by its ability to judge whether the
natural language sentences are in not in line with common sense and what are those reasons. To evaluate
the model, three subtasks are designed. Subtask A is the validation task in which two statements with
similar structure are given, and task is to discern which statement makes sense and which statement does
not. Subtask B is the Explanation task where the multiple choices (three options) have been provided, to
choose the reason that is most likely to explain a statement that doesn’t makes sense. Subtask C is about
generating the explanation for non-common sense statements.

Natural Language Understanding has drawn a tremendous amount of research attention recently.
Although some well-performed end-to-end model even show better performances than humans on some
benchmark, they are still far from human on common sense. If a model lack of a common sense processes
data that requires common sense, the performance of the model may drop dramatically, which is the sign
for the poor robustness. Therefore, the importance of commonsense reasoning is not only confined to
natural language understanding system, it should also be expanded to the other systems.

Many similar tasks have been worked on before this task was proposed. Previous attempts of solving
the common sense challenge involve the utilization of annotated knowledge bases, rule based reasoning
or the hand crafted features. By the time, the advantages of the knowledge base gradually emerged from
the methods, and researchers are more inclined to use this method to solve the problems. Using the
annotated knowledge bases is an expensive approach whereas the unsupervised training done on the text
corpora which is cheap. Now-a-days, the neural LMs have achieved the great success, being used as the
feature representations for a sentence.

It is observed that the results of some models are similar and some of them are different. This reflects
to the different structure of different models, the training time and the training data, etc. Therefore, the
performance can be improved by ensemble learning for only complementary models can correct each
other to get better results. Our best model achieved in official test evaluation accuracy of 95% for subtask
A. In addition, I also made a comprehensive analysis of the data of the task A. I found that data can be
classified by the structure of the sentence since the dataset of task A can be divided into three categories
explained later. My model does not deal with different types of data with different approaches separately,
but the future model proposed for these characteristics may better solve the task.

# Methods

## Open - AI GPT

Open-AI GPT model a unidirectional pre-trained model with language modelling on the Toronto
Book Corpus which is the large dataset having the long range of dependencies in it. Model
probability is based on the next word in the sequence. The basic transformer on head model is
very effective in predicting the next token based on the current word. The models calculates the
perplexity score, based on does this sentence makes any sense or not. The higher the score is,
less plausible the sentence would be and would be against the common sense. The model choses
the sentences with high perplexity score, which means its working fine! But lacks the word
representation performance.

## BERT
The second approach we used is the BERT model. This model uses the bidirectional encoder
representations form which is one of the state-of-art neural network language model. It is trained
by bulk amount of un-labeled data and uses the transfer learning to the labeled data. This model
can capture the broader context on sentences. We have loaded the model and the BERT tokenizer.
Pre- trained the model with bull of data. It produces the low logit scores for the sentences that are
against the common sense and logit scores calculations are based on the labels of the data.
In this method, I have dealt with fine tuning BERT using ktrain. Ktrain is lightweight
wrapper for the deep learning library Tensorflow Keras and many other libraries, which help to
build, train and deploy neural networks and many other machine learning models. It provides the
support for applying many pre-trained deep learning architectures in the domain of NLP and
BERT is one of them. To solve this problem of common sense validation, I have used the
implementation of pre-trained BERT provided by ktrain and fine-tune it to classify whether the
sentence makes sense or not.

# Data Analysis
After trying many parameter and ensembling many fine tune model, the score on
developing/validation dataset became steady. After working on dataset and checking it case by
case, I found that the samples of dataset can be classified into 3 of its types:
- Only the single difference of entities, actions and activities is found among the wrong and
correct ones.
- The replacement of keywords leads to the ambiguity in the meaning of the sentence.
- These samples have no obvious characteristics in them. Same subject is being used but the
expression of the sentence is completely different from the other one, while the others are
completely different things.
So, the initial two of the examples having the clear structure and meaning stand out for most of
the dataset. Therefore, the performance could be improved on processing the certain type of
confusing samples.

# Experiments and Results

For Open-AI GPT Head model, I got the accuracies of 80.2%, 72.5% and 73.5% for training,
validation and test data respectively.
For the BERT model I have got the accuracies of 95.54 %, 96.53%, 96.52% for training,
validation and test dataset respectively.

# Conclusion
The ability of common sense validation and explanation is very important for most models. This
will directly affect the rationality of the generated model output. The bulk amount and diversity
of common sense poses great challenges to this task. The current neural network models are often
data-driven, while the annotated data is often limited and requires a lot of manual labeling. In
such case, we proposed transfer learning to handle this challenge. From my experiments, I can
draw the following three main conclusions:
- Neural language model fully qualified for commonsense validation and explanation. We
attribute this to the powerful word and sentence representation capabilities of language models.
- The inconsistency of task of pre-training and fine-tuning will badly hurt the performance.
- A larger amount of data and more parameters will enhance the common sense of the model. At
the same time, the content of the data is equally important.
I identified how easy it is to implement a complex model BERT into common sense validation
domain using ktrain. In the end, I am able to achieve the accuracy of around 96.52%.
