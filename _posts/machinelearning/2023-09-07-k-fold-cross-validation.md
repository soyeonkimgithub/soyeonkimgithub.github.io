---
layout: post
title: k-Fold Cross Validation
categories: machinelearning
sitemap: false
hide_last_modified: true
published: true
---
## [ML] k-Fold Cross Validation

### background

In machine learning, we couldn’t fit the model on the training data and can’t say that the model will work accurately for the real data. For this, we must assure that our model got the correct patterns from the data, and it is not getting up too much noise. For this purpose, we use the cross-validation technique.

### description

- Cross validation is a technique used to evaluate the performance of a model on unseen data
- There are several types of cross validation techniques, including k-fold, leave-one-out, stratified cross validation.
- k-fold cross validation
    - shuffle the dataset randomly
    - split the dataset into k groups
    - for each unique group
        - take the group as a test data set
        - take the remaining groups as a training data set
        - fit a model on the training set and evaluate it on the test set
        - retain the evaluation score and discard the model
    - summarise the skill of the model using the sample of model evaluation score

### how to use
~~~python
from sklearn import cross_validation
# value of K is 10.
data = cross_validation.KFold(len(train_set), n_folds**=**10, indices**=**False)
~~~