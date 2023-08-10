---
layout: post
title: Evalution
categories: study
sitemap: false
hide_last_modified: true
published: true
---
## [ML] Evalution

### Regression Evaluation Metrics

| $${y-test}$$ | $${prediction}$$ | $${diff}$$ | &#124;$${diff}$$&#124; | $${diff}^2$$ |
|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|
| 98          | 100         | +2          | 2           | 4 |
| 100         | 102         | +2          | 2           | 4 |
| 102         | 100         | -2          | 2           | 4 |
| 95          | 94          | -1          | 1           | 1 |
| 90          | 89          | -1          | 1           | 1 |
| | | sum = 0 | sum = 8 | sum=14 |

#### 1. Mean Absolute Error (MAE) : $$\frac 1n\sum_{i=1}^n|y_i-\hat{y}_i|$$
* MAE = 8/5 = 1.6
* average error

#### 2. Mean Squared Error (MSE) : $$\frac 1n\sum_{i=1}^n(y_i-\hat{y}_i)^2$$
* MSE = 14/5 = 2.8
* relatively big as it's squared (-> scale problem)
* 'punishes' larger error, useful  

#### 3. Root Mean Squred Error (RMSE) :  $$\sqrt{\frac 1n\sum_{i=1}^n(y_i-\hat{y}_i)^2}$$
* adjust scale
* interpretable in the 'y' units


| y-test      | prediction  | $${diff}^2$$ |
|:-----------:|:-----------:|:-----------:|
| 98          | 100         | 4 |
| 100         | 102         | 4 |
| 102         | 100         | 4 |
| 95          | 94          | 1 |
| 90          | 89          | 1 |
| | | RMSE = 1.67|

| y-test      | prediction  | $${diff}^2$$ |
|:-----------:|:-----------:|:-----------:|
| 980         | 1,000       | 400 |
| 1,000       | 1,020       | 400 |
| 1,020       | 1,000       | 400 |
| 950         | 940         | 100 |
| 900         | 890         | 100 |
| | | RMSE = 16.7|

* RMSE cannot be compared between different dataset
* can be used for comparing different model with same dataset

#### 4. $${R}^2$$
* how good that guess will be
* i.e. 0.6 -> there is a 60% reduction in variance when we take the x feature into account
* x feature 'explains' 60% of the variation in y
* measured with training set not new data
![evaluation-1](/assets/img/post/study/RSquared.png){:width="20%" :.centered loading="lazy"}

----
### Confusion Matrix
1. easy to use
2. easy to explain
3. predict continuous variable
----
1. find the breach problem presentation
2. post regarding the evaluation
3. post regarding the linear regression


