---
layout: post
title: Linear Regression
categories: study
sitemap: false
hide_last_modified: true
published: true

---
## [Algorithm] Linear Regression

### Linear Regression
* Predict continuous numeric values (i.e. given characteristics of a car predict mileage, given location and attributes of a home predict price, given GDP, health indicators predict life expectation)
* Given some data that we think are related, 
1. Quantifies the relationship in the data ($${R}^2$$)
2. Determines how reliable that relationship is (p-Value)
* y = wx + b (w : regression coefficients, weights, slope, b : y-intercept, outcome value when all features are 0)

~~~python
from sklearn.linear_model import LinearRegression
lm = LinearRegression()
lm.fit(X_train, y_train)
predictions = lm.predict(X_test)
~~~

### Gradient decent
* a way of optimise (minimise loss function)
* pick a random value -> find the slope of that point (we can use tangent line to observe the steepness of the slope) -> updates to the weight (depending on the steepness which is learning rate) -> the slope gradually reduce until it reaches the lowest point on the curve (the point of convergence)
* a differential coefficient (미분계수)
* lowest sum of squared residuals

### p-Value
