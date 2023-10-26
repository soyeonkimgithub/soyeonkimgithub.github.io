---
layout: post
title: Precision and Recall
categories: machinelearning
sitemap: false
hide_last_modified: true
published: true
---
## [ML] Precision and Recall

### background

This is one of performance metrics to evaluate model for binary classification problem.

### description

- Precision
    - What proportion of positive identifications was actually correct?
    - positive predictive value
    - TP / TP + FP
- Recall
    - What proportion of actual positives was identified correctly?
    - true positive rate
    - TP / TP + FN
- F1 score
    - the harmonic mean of precision and recall
    - 2(P*R)/(P+R)
    - works well with an imbalanced dataset
    - the higher the better

### how to use

- If there is a requirement of classifying all positive as well as Negative samples as Positive, whether they are classified correctly or incorrectly, then use Precision.
- Further, on the other end, if our goal is to detect only all positive samples, then use Recall. Here, we should not care how negative samples are correctly or incorrectly classified the samples.