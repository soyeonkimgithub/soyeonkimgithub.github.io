---
layout: post
title: Breach Detection for Dynamic Tolerance
image: 
  path: /assets/img/blog/jeremy-bishop@0,5x.jpg
description: >
  This is personal project for knoweledge sharing session in company. I experimented and implemented one of the hypothesis as an extension of the NAV-POC. 
category: project
hide_last_modified: true
published: true
---
## [Personal]Breach Detection for Dynamic Tolerance

### Summary
* Task: Predict tomorrow's volatility using AWS SageMaker
* Data: historical price and VIX of "Coca-Cola" from 01/Jan/2010 ~ 11/Feb/2023 retrieved from yahoo finance
* Tools: Python, AWS SageMaker
* ML Algorithms: XGBoost
* Evaluation metrics: RMSE

### Key Points
1. I used each of the machine learning process in SageMaker; from getting built-in algorithm, training, model tuning, deploying and using model by lambda. 
2. Automatic Model Tuning improves result.
3. It tends to follow the recent time window.
4. ARIMA might be better for precition.

{:.text-align-center}
![400x200](/assets/img/post/project/volatility_inference01.png){:width="45%"}
![400x200](/assets/img/post/project/volatility_inference02.png){:width="45%"}

Pass today's volatility 0.301 and get predicted volatility -0.399

### Results
MSE slightly decreased from 1.29 to 1.13 after Automatic Model Tuning

### Download
* <a href="https://github.com/soyeonkimgithub/Volatility-Forecasting/blob/main/Security_Volatility_Forecast.pptx">presentation ppt</a>
* <a href="https://github.com/soyeonkimgithub/Volatility-Forecasting/blob/main/volatility_forecasting.ipynb">code</a>

### Code
<iframe src="https://nbviewer.org/github/soyeonkimgithub/Volatility-Forecasting/blob/main/volatility_forecasting.ipynb" width="1000" height="1500" scrolling="yes" frameborder="1"></iframe>
