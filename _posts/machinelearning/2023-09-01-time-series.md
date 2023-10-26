---
layout: post
title: Evalution
categories: machinelearning
sitemap: false
hide_last_modified: true
published: true
---
## [ML] Time Series

### background

time series is not randomly distributed data, it is inherently ordered by chronological order. If a pattern emerges in later time periods for example, your model may still pick up on it even if that effect doesn’t hold in earlier year. 

### description

- validation
    - forward chaining where you’ll be able to model on past data then look at forward-facing data.
    - fold 1: training 1, test 2
    - fold 2: training 1, 2, test 3
    - fold 3: training 1,2,3, test 4
- stationary? → it is stationary when the variance, covariance, and mean of the series are constant with time. Augmented Dickey-Fuller test can be used
- ARIMA model → Autoregressive Integrated Moving Average
    - p : the order of autoregressive model (past values, number of time lags)
    - d : the degree of differencing (the number of times the data have had past values subtracted)
    - q : the order of moving-average model
- persistence model : assumes that the future value of a time series is calculated under the assumption that nothing changes between the current time and the forecast time