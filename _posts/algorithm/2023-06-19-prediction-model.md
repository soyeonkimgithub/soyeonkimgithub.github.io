---
layout: post
title: Algorithm 
categories: study
sitemap: false
hide_last_modified: true
published: true
---

## [Algorithm] Traditional Prediction Models

### AR(1)
- If I want predict a value of the time series on some given day, I can use that time series lagged 1 day prior. 
I can predict where I will be tomorrow, based on where I am today.
- Today's value = C1 * Yesterday's value + Today's error

### ARMA(1,1)
- AR(1) + previous day's error
- Today's value = C1 * Yesterday's value + C2 * Yesterday's error + Today's error

### ARCH(1)
- Take into account the volatility or how far away that time series is jumping to predict next value
If I'm jumping a lot today (if my time series is very volatile today), it's probably going to also pretty volatile tomorrow. If it's very steady today, it will probably be very steady tomorrow as well. 
- Today's value = root(C1 * Yesterday's value squre) * Today's error
- Today's value = Today's volatility * Today's error
- Problem: bursty (it's constant and then it is jump, and then it goes back to the regural state)

### GARCH(1)
- My volatility today is affected by the value of my time series yesterday but also my volatility yesterday.
- Today’s value = root(C1 * Yesterday’s value square + C2 * Yesterday’s volatility square) * Today’s error

### Regressive
predicts future values based on past values

### Autoregressive
autoregressive models are based on the assumption that past values have an effect on current value
