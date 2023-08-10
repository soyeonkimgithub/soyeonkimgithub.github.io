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
1. Mean Absolute Error (MAE) 
- average error

$$
\begin{aligned} %!!15
  \phi(x,y) &= \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right) \\[2em]
            &= \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j)            \\[2em]
            &= (x_1, \ldots, x_n)
               \left(\begin{array}{ccc}
                 \phi(e_1, e_1)  & \cdots & \phi(e_1, e_n) \\
                 \vdots          & \ddots & \vdots         \\
                 \phi(e_n, e_1)  & \cdots & \phi(e_n, e_n)
               \end{array}\right)
               \left(\begin{array}{c}
                 y_1    \\
                 \vdots \\
                 y_n
               \end{array}\right)
\end{aligned}
$$

2. Mean Squared Error (MSE) 
- 'punishes' larger error, useful  

3. Root Mean Squred Error (RMSE) : 
- interpretable in the 'y' units

4. 

### RMSE
1. binary classification
2. easy to translate (based on linear regression)
3. used activation function in deep learning 


1. find the breach problem presentation
2. post regarding the evaluation
3. post regarding the linear regression


