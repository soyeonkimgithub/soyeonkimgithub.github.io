---
layout: post
title: Multicollinearity 
categories: machinelearning
sitemap: false
hide_last_modified: true
published: true
---

## [ML] Multicollinearity

### background

Multicollinearity occurs when there are two or more independent variables in a multiple regression model which have a high correlation among themselves. When some features are highly correlated, we might have difficulty in distinguishing between their individual effects on the dependent variable. Multicollinearity can be detected using Variance Inflation Factor (VIF).

i.e listening music and jogging → which will have a greater impact on fitness?

(https://www.geeksforgeeks.org/test-of-multicollinearity/?ref=gcse)

### description

- Variance Inflation Factor (VIF)
    - we pick each feature and regress it against all of the other features.
    - VIF = 1/1-R^2
    - Higher R-squared → greater VIF → stronger collinearity
    - generally, VIP above 5 indicates a high multicollinearity

### how to use
~~~python
from statsmodels.stats.outliers_influence import variance_inflation_factor
# creating dummies for gender
data['Gender'] = data['Gender'].map({'Male':0, 'Female':1})

# the independent variables set
X = data[['Gender', 'Height', 'Weight']]

# VIF dataframe
vif_data = pd.DataFrame()
vif_data["feature"] = X.columns

# calculating VIF for each feature`
vif_data["VIF"] = [variance_inflation_factor(X.values, i) for i in range(len(X.columns))]
~~~