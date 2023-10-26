---
layout: post
title: L1 and L2 Regularisation
categories: machinelearning
sitemap: false
hide_last_modified: true
published: true
---
## [ML] L1 and L2 Regularisation

### background

“Regularisation” - information is added to an objective function.

We want to add some bias into our model to prevent it overfitting.

### description

- L1 Regularisation
    - Lasso Regression
    - adds the ‘absolute value of magnitude’ of the coefficient as a penalty term to the loss function
    - shrink coefficient to zero → feature selection
    - robust on outlier
    - not good for gradient-based learning
- L2 Regularisation
    - Ridge Regression
    - adds the ‘squared magnitude’ of the coefficient as the penalty term to the loss function
    - shrink coefficient evenly → useful when you have collinear/codependent feature
    - sensitive on outlier (as it’s squared)
    - allow weight decay (preventing certain weights getting too large)
    - better result than L1

### how to use

~~~python
from sklearn.linear_model import LinearRegression, Ridge, Lasso

# Loop to compute the different values of cross-validation scores - Ridge
for i in range(1, 9):
    ridgeModel = Ridge(alpha = i * 0.25)
    ridgeModel.fit(X_train, y_train)
    scores = cross_val_score(ridgeModel, X, y, cv = 10)
    avg_cross_val_score = mean(scores)*100
    cross_val_scores_ridge.append(avg_cross_val_score)
    alpha.append(i * 0.25)

# Loop to compute the cross-validation scores` - Lasso
for i in range(1, 9):
    lassoModel = Lasso(alpha = i * 0.25, tol = 0.0925)
    lassoModel.fit(X_train, y_train)
    scores = cross_val_score(lassoModel, X, y, cv = 10)
    avg_cross_val_score = mean(scores)*100
    cross_val_scores_lasso.append(avg_cross_val_score)
    Lambda.append(i * 0.25)
~~~