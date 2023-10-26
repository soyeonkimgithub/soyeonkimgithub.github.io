---
layout: post
title: Handle Missing Data
categories: machinelearning
sitemap: false
hide_last_modified: true
published: true
---

## [ML] Handle Missing Data

### background

| Deletion | Deleting Rows |  |  |
| --- | --- | --- | --- |
|  | Pairwise Deletion |  |  |
|  | Deleting Columns |  |  |
| Imputation | Time-Series Problem | Data without Trend & without Seasonality | Mean, Median, Mode, Random Sample Imputation |
|  |  | Data with Trend & without Seasonality | Linear Imputation |
|  |  | Data with Trend & with Seasonality | Seasonal Adjustment Imputation |
|  | General Problem | Categorical | Make N/A as level, Multiple Imputation, Logistic Regression |
|  |  | Continuous | Mean, Median, Mode, Multiple Imputation, Linear Regression |

### description

- If the data set is large, delete
    1. deleting rows that are missing values
    2. pairwise deletion analyses all causes in which the variables of interest are present and thus maximises all data available by an analysis basis
    3. delete columns that are missing data
- for smaller data set, we can impute missing values. If the data is time series we interpolate the missing data depending on whether the time series has trend and seasonality. For general continuous data we can use the mean, median, mode, multiple imputation and linear regression to fill in the missing values.
- for general categorical problem we can
    1. Mode imputation is one method but it will definitely introduce bias → most frequent value
    2. Missing values can be treated as a separate category by itself. → simplest
    3. Prediction models: we can create a predictive model to estimate values that will substitute the missing data. We divide our data set into two sets: once set with no missing values for the variable(training) and another one with missing values(test). We can use logistic regression and ANOVA for prediction
    4. Multiple imputation : this is a general approach to the problem of missing data that is available in several commonly used statistical packages. It aims to allow for the uncertainty about the missing data by creating several different plausible imputed data sets and appropriately combining results obtained from each of them.

### how to use