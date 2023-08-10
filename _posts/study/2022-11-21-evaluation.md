---
layout: post
title: Evalution
categories: study
sitemap: false
hide_last_modified: true
published: true
---
## [ML] Evalution

## Regression Evaluation Metrics
Regression is a task when a model attempts to predict continuous values

| $${y-test}$$ | $${prediction}$$ | $${diff}$$ | &#124;$${diff}$$&#124; | $${diff}^2$$ |
|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|
| 98          | 100         | +2          | 2           | 4 |
| 100         | 102         | +2          | 2           | 4 |
| 102         | 100         | -2          | 2           | 4 |
| 95          | 94          | -1          | 1           | 1 |
| 90          | 89          | -1          | 1           | 1 |
| | | sum = 0 | sum = 8 | sum=14 |

### 1. Mean Absolute Error (MAE) : $$\frac 1n\sum_{i=1}^n|y_i-\hat{y}_i|$$
* take the difference between the true value minus predicted value, and take the absolute value because predictions could be over or under, then average that out for all predicted values
* MAE = 8/5 = 1.6
* average error

### 2. Mean Squared Error (MSE) : $$\frac 1n\sum_{i=1}^n(y_i-\hat{y}_i)^2$$
* take the difference the true and predicted value, and square it, then the larger errors are noted more than with MAE
* MSE = 14/5 = 2.8
* 'punishes' your model for those outlier situation that it's not fitting to
* relatively big as it's squared -> scales units too, difficult to interpret

### 3. Root Mean Squred Error (RMSE) :  $$\sqrt{\frac 1n\sum_{i=1}^n(y_i-\hat{y}_i)^2}$$
* most popular because it punishes those larger error value and adjusts scale (interpretable in the 'y' units)
* cannot be used for comparing between different dataset like below

| $${y-test}$$ | $${prediction}$$ | $${diff}^2$$ |
|:-----------:|:-----------:|:-----------:|
| 98          | 100         | 4 |
| 100         | 102         | 4 |
| 102         | 100         | 4 |
| 95          | 94          | 1 |
| 90          | 89          | 1 |
| | | RMSE = 1.67|

| $${y-test}$$ | $${prediction}$$ | $${diff}^2$$ |
|:-----------:|:-----------:|:-----------:|
| 980         | 1,000       | 400 |
| 1,000       | 1,020       | 400 |
| 1,020       | 1,000       | 400 |
| 950         | 940         | 100 |
| 900         | 890         | 100 |
| | | RMSE = 16.7|

* can be used for comparing different model with same dataset
* cannot explain 'is this good enough?'

### 4. $${R}^2$$
* how good that guess will be
* i.e. 0.6 -> there is a 60% reduction in variance when we take the x feature into account
* x feature 'explains' 60% of the variation in y
* measured with training set not new data

![evaluation-1](/assets/img/post/study/RSquared.png){:width="20%" :.centered loading="lazy"}

## Classification Evaluation Metrics
Classification is a task when a model attempts to predict categorical values (binary or multi)
* either your model is correct or incorrect in its prediction

### 1. Accuracy
* number of correct predictions / total number of predictions
* useful when target classes are well balanced

### 2. Recall
* ability of a model to find all the relevant cases within a dataset
* number of true positive / (number of true positive + number of false negative)

### 3. Precision
* ability of a model to identify only the relevant data points
* number of true positive / (number of true positive + number of false positive)

### 4. F1-Score
* trade-off between recall and precision
* recall expresses the ability to find all relevant instances in a dataset
* precision expresses the proportion of the data points our model says was relevant that actually were relevant
* optimal blend of precision and recall
* harmonic mean of precision and recall -> punishes extreme value
* $$F_{1} = {2* {(precision*recall)}\over(precision+recall)}$$

### 5. Confusion matrix
* organise our predicted values compared to the real values 
![evaluation-2](/assets/img/post/study/ConfusionMatrix.png){:width="30%" :.centered loading="lazy"}
