---
layout: post
title: Volatility Forecast with Sagemaker
description: >
  Volatility Forecast
  This project is based on the World Happiness report which was released in 2017 and ranks 155 countries by their levels of happiness.
  Volatility Forecasting using AWS SageMaker
category: project
hide_last_modified: true
published: true
---
## [Personal]Volatility Forecast with Sagemaker

### Summary
* Task: Predict tomorrow's volatility using AWS SageMaker
* Data: historical price and VIX of "Coca-Cola" from 01/Jan/2010 ~ 22/Feb/2023 retrieved from yahoo finance
* Tools: Python, AWS SageMaker
* ML Algorithms: XGBoost
* Evaluation metrics: RMSE

### Key Points
1. use each of the machine learning process in SageMaker; from getting built-in algorithm, training, model tuning, deploying and using model by lambda 
2. resources
3. Constraints : look into just one security, does not explain different domain
4. Why Standardisation?
5. What Did I Find?
6. Result?

{:.text-align-center}
![400x200](/assets/img/post/project/volatility_inference01.png){:width="45%"}
![400x200](/assets/img/post/project/volatility_inference02.png){:width="45%"}

Pass today's volatility 0.301 and get predicted volatility -0.399

### Results
MSE slightly decreased from 1.29 to 1.13 after Automatic Model Tuning

### Download
* <a href="https://github.com/soyeonkimgithub/Volatility-Sagemaker/blob/main/Volatility_Forecast_Sagemaker.pptx">presentation ppt</a>
* <a href="https://github.com/soyeonkimgithub/Volatility-Sagemaker/blob/main/xgboost_volatility_forecast.ipynb">code</a>

### Code
<iframe src="https://nbviewer.org/github/soyeonkimgithub/Volatility-Sagemaker/blob/main/xgboost_volatility_forecast.ipynb" width="1000" height="1500" scrolling="yes" frameborder="1"></iframe>




