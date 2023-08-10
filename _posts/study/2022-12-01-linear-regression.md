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


### Gradient decent
* a way of optimise (minimise loss function)
* pick a random value  하고 그 점에 대한 편(partial)미분값 구하면 접선에 대한 기울기를 구하는데 음수면 오른쪽으로 양수면 왼쪽으로 해서 점점 최소 에러값 찾아서 가. 기울기(얼마나 멀리 뛰는지, learning rate)
* a differential coefficient (미분계수)
* lowest sum of squared residuals

### p-Value
