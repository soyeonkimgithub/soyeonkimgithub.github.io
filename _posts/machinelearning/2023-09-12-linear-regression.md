---
layout: post
title: Linear Regression 
categories: machinelearning
sitemap: false
hide_last_modified: true
published: true
---

## [ML] Linear Regression

### background

The simplest machine learning algorithm of predictive analysis. It shows linear relationship between a dependent and one or more independent variables. It finds how the value of the dependent variable is changing according to the value of the independent variable. It makes predictions for continuous or numeric variables.

### description

- Assumption
    1. The sample data used to fit the model representative of the population
    2. The relationship between X and the mean of Y is linear
    3. The variance of the residual is the same for any value of X 
        
        → Homoscedasticity of Residuals or Equal Variances
        
        → the spread residuals which we are getting from the linear regression model should be homogeneous or equal space
        
    4. Observations are independent of each other
    5. For any value of X, Y is normally distributed
- Extreme violation of these assumption will make the results redundant. Small violation of these assumptions will result in a greater bias or variance of the estimate.

### how to use
~~~python
from sklearn.linear_model import LinearRegression
lm = LinearRegression()
lm.fit(X_train, y_train)
predictions = lm.predict(X_test)
~~~