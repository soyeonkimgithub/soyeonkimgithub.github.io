---
layout: post
title: Gradient Descent
categories: machinelearning
sitemap: false
hide_last_modified: true
published: true
---

## [ML] Gradient Descent

### background

In any machine learning project our main aim relies on how good our project accuracy is or how much our model prediction differs from the actual data point. Based on the difference between model prediction and actual data points we try to find the parameters of the model which give better accuracy on our dataset. In order to find these parameters we apply gradient descent on the cost function of the machine learning model.

### description

- is an iterative optimisation algorithm that tries to find the optimum value of an objective function.
- steps
    - pick a random value
    - find the slope of that point (use partial differentiation)
    - update to the weight (depending on learning rate → steepness)
    - the slope gradually reduce until it reaches the lowest point on the curve → the point of convergence → lowest sum of squared residuals
- SGD (Stochastic Gradient Descent)
    - Both GD, SGD, you update a set of parameters in an iterative manner to minimise an error function
    - GD: run through all the samples in training set to do a single update for a parameter in a particular iteration.
    - SGD: only one or subset of training sample from training set to do the update for a parameter in a particular iteration.
    - if use subset → it is called minibatch stochastic gradient descent
- Gradient Descent minimises the error function better than Stochastic Gradient Descent.
- SGD converges much faster once the dataset becomes large.
- GD is preferable for small datasets while SGD is preferable for larger ones.
- SGD is used for most applications because it minimises the error function well enough while being much faster and more memory efficient for large datasets.
- Batch size
    - Hyperparameter which controls how many data points to train on before updating the model’s parameters
    - Batch Gradient Descent (batch size = size of training set)
    - Stochastic Gradient Descent (batch size=1)
    - Mini-batch Gradient Descent (1 < batch size < size of training set)