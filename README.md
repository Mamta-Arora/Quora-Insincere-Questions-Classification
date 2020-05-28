# Quora Insincere Questions Classification

## Problem Description:

[Quora](Http://quora.com) is a good question answering website. People Are producing, sharing and looking up helpful contents but meanwhile, some people use it to promote hatred and violence against individuals or groups based on race, religion, sexual orientation, etc.

We explored different **Machine Learning** approaches and built a text classification predictive model to **detect inappropriate texts**. By filtering inappropriate contents, users with questions feel happier and easier to ask and find information they need hence they will be more active.

## Steps

### Explore Data

1. A csv file with two columns: 

* `qid`: Question id (str)
* `question`: The question content(str)
* `target`: Label for toxic or nontoxic(bool)

2.  Data size: 1.3 millions * 3 
3. Data is heavily imbalanced: 94% of texts are non-toxic and 6% are toxic.

4.  Sincere questions are more about technology, material life, emotional need; Insincere questions are more about race, religion, politics. 

 <img src="https://github.com/ReinaFeng/Quora-Insincere-Questions-Classification/raw/master/image/topwords.png" alt="topwords.png" style="zoom: 33%;" /> 

### Models

#### Logistic Regression Classifier

* Vectorize: TF-IDF

#### Neural Network Classifier

* Vectorize: Word-Embeddings

* Embedding Models:

  We didn't use standard preprocessing steps like stemming or stop word removal when you have pre-trained embeddings.

  <img src="https://github.com/ReinaFeng/Quora-Insincere-Questions-Classification/raw/master/image/1.png" alt="1.png" style="zoom: 50%;" />

   Compare different pre-train:<img src="https://github.com/ReinaFeng/Quora-Insincere-Questions-Classification/raw/master/image/2.0.png" alt="2.0.png" style="zoom:50%;" /> 

  Compare different embedding performance:

   <img src="https://github.com/ReinaFeng/Quora-Insincere-Questions-Classification/raw/master/image/3.png" alt="3.png" style="zoom:50%;" /> 

* Preprocessing: 

  Fill in missing value by “_na_”
  Tokenize
  Padding(fix length or variable length)
  Embedding Matrix

* Models: 

  * 2-layer BiGRU

  * LSTM+CNN
  * GRU+Attention

  

### Evaluation

#### Performance

Since the data is imbalanced, 94% are the sincere target, so accuracy for four models are both high, but through the F1 score, could find the LR model is not good.

 <img src="https://github.com/ReinaFeng/Quora-Insincere-Questions-Classification/raw/master/image/6.png" alt="6.png" style="zoom: 33%;" /> 

#### Look at Result

Compared to LR Model, these texts are correctly predicted by this DL model.

 <img src="https://github.com/ReinaFeng/Quora-Insincere-Questions-Classification/raw/master/image/8.png" alt="8.png" style="zoom: 50%;" /> 

Misclassifies - it is hard to predict for human too:

  <img src="https://github.com/ReinaFeng/Quora-Insincere-Questions-Classification/raw/master/image/9.png" alt="9.png" style="zoom:50%;" /> 