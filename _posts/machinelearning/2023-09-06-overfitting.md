---
layout: post
title: Overfitting
categories: machinelearning
sitemap: false
hide_last_modified: true
published: true
---
## [ML] Overfitting

### background

There are three main methods to avoid overfitting.

### description

- keep the model simpler
    
    → reduce variance by taking into account fewer variables and parameters thereby removing some of the noise in the training data
    
- use cross-validation techniques such as k-folds cross-validation
- use regularisation techniques such as LASSO that penalise certain model parameters if they’re likely to cause overfitting