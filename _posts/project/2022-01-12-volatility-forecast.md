---
layout: post
title: Volatility Forecast 
image: 
  path: /assets/img/post/project/Security_02.png
description: >
  This is personal project for knoweledge sharing session in company. I used XGBoost for prediction and compare with GARCH model.
category: project
hide_last_modified: true
published: true
---
## [Personal]Volatility Forecast

### Summary
* Task: Predict tomorrow's volatility 
* Data: historical price and VIX from 01/Jan/2010 ~ 11/Feb/2023 retrieved from yahoo finance
* Tools: Python, GARCH
* ML Algorithms: XGBoost
* Evaluation metrics: RMSE

### Key Points
1. Compare traditional GARCH model and XGBoost for prediction of security's volatility. 
2. XGBoost is better than GARCH especially for high volatile security.

### Results
XGBoost RMSE for less volatile security (Coca-Cola) is 1.10 which is better than traditional GARCH models' 1.58.
For more volatile security (Tesla), XGBoost RMSE is 1.16 that is way better than GARCH's 5.61. 

### Download
* <a href="https://github.com/soyeonkimgithub/Volatility-Forecasting/blob/main/Security_Volatility_Forecast.pptx">presentation ppt</a>
* <a href="https://github.com/soyeonkimgithub/Volatility-Forecasting/blob/main/volatility_forecasting.ipynb">code</a>

### Code
<iframe src="https://nbviewer.org/github/soyeonkimgithub/Volatility-Forecasting/blob/main/volatility_forecasting.ipynb" width="1000" height="1500" scrolling="yes" frameborder="1"></iframe>
