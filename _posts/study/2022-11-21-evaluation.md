---
layout: post
title: Evalution
categories: study
sitemap: false
hide_last_modified: true
published: true

---

## [ML] Evalution

### Confusion Matrix
1. easy to use
2. easy to explain
3. predict continuous variable

### Regression Evaluation Metrics

| actual  | predicts |  diff  | |diff|  |  diff^2  |  
|---------|:---------|:------:|:-------:|:--------:|
|   98    |    100   |   +2   |    2    |     4    |   
|   100   |    102   |   +2   |    2    |     4    |   
|   102   |    100   |   -2   |    2    |     4    | 
|   95    |    94    |   -1   |    1    |     1    |  
|   90    |    89    |   -1   |    1    |     1    |   

1. Mean Absolute Error (MAE) : $$\frac 1n\sum_{i=1}^n|y_i-\hat{y}_i|$$
- average error
- metrics.mean_absolute_error(y_test, predictions)


2. Mean Squared Error (MSE) : $$\frac 1n\sum_{i=1}^n(y_i-\hat{y}_i)^2$$
- 'punishes' larger error, useful  
- metrics.mean_squared_error(y_test, predictions)


3. Root Mean Squred Error (RMSE) :  $$\sqrt{\frac 1n\sum_{i=1}^n(y_i-\hat{y}_i)^2}$$
- interpretable in the 'y' units
- np.sqrt(metrics.mean_squared_error(y_test, predictions))


4. $${R}^2$$
- metrics.explained_variance_score(y_test, predictions)



1. find the breach problem presentation
2. post regarding the evaluation
3. post regarding the linear regression


