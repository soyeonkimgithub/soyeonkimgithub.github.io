---
layout: post
title: Bias-Variance Tradeoff
categories: machinelearning
sitemap: false
hide_last_modified: true
published: true
---
## [ML] Bias-Variance Tradeoff

### background

There are various way to evaluate model. We can use MSE for Regression, Precision, Recall and Absolute Error for Classification. In a similar way, Bias and Variance help us in parameter tuning, and deciding better-fitted models.

### description

- find a good balance between underfitting and overfitting
- bias and variance are type of error, reducible error
- bias
    - one type of error occurs due to wrong assumption
    - assuming data is linear, but data actually follows a complex function
    - there is some difference/error occurring between the model’s predicted value and actual value → knows as bias error or error due to bias
    - systematic error → data is skewed in standardised ways
    - simply defined as the inability of the model
- variance
    - is the amount by which the performance of a predictive model changes when it is trained on different subsets of the training data
    - how much it is sensitive to another subset of the training dataset
    - high variance: the model performs well on the training data but poorly on new unseen test data → overfitting

### how to use

- high bias
    - make model complex i.e. increasing the number of hidden layers
    - increase the number of features to capture the underlying patterns in the data
    - reduce regularisation of the model
    - increase the size of training data
- high variance
    - cross-validation: by splitting data multiple times, this can help identify if a model is overfitting or underfitting
    - feature selection: by choosing the relevant feature, will decrease model complexity
    - regularisation: L1, L2 regularisation to reduce variance in model
    - ensemble methods: combine multiple models to improve generalisation performance. bagging, boosting and stacking are common ensemble methods
    - simplifying the model i.e. decreasing the number of parameters or layers in neural network
    - early stopping