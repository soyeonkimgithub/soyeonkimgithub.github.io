---
layout: post
title: Logistic Regression
categories: study
sitemap: false
hide_last_modified: true
published: true
---
## [Algorithm] Logistic Regression

### Logistic Regression
* classify input data into categories (i.e. spam or ham, buy or sell or hold, cat or dog or mouse, positive text or negative or neutral)
* predict discrete categories; classification problem
* the result is probability between 0 and 1
* easy to translate (based on linear regression)
* used as an activation function in deep learning 

~~~python
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import classification_report
from sklearn.metrics import confusion_matrix

logmodel = LogisticRegression()
logmodel.fit(X_train, y_train)
predictions = logmodel.predict(X_test)

print(classification_report(y_test,predictions))
confusion_matrix(y_test, predictions)
~~~

----
### Decision Tree
1. can be used in various problems
2. visualisation
3. based on latest algorithm 

### Random Forerst
1. fix overfitting and can be used in various problems
2. based on ensembles
3. good prediction

### Kmeans Clustering
1. unsupervised model
2. segmentation

#### XGBoost
1. one of tree model
2. 


clustering 
- discover patterns and groupings in data
- document discovery: find all documents related to homicide cases, social media ad targeting: find all users who are interested in sports

dimensionality reduction 
- find latent or significant features in data
- find latent drivers of stock movements
- pre-process data to build more robust machine learning models
- improve performance of models

looks like people that did not survive were much more likely to be male 
multi-collinearity

----
