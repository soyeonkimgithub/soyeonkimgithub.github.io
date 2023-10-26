---
layout: post
title: Clustering
categories: literature
sitemap: false
hide_last_modified: true
published: true

---
## [ML] Clustering

## Clustering Time Series Data through Autoencoder-based Deep Learning Models
* Goal : introduces a two-stage method for clustering time series data. First, a novel technique is introduced to utilise the characteristics (e.g., volatility) of given time series data in order to create labels and thus be able to transform the problem from unsupervised learning into supervised learning. Second, an autoencoder-based deep learning model is built to learn and model both known and hidden features of time series data along with their created labels to predict the labels of unseen time series data.
* Link : https://arxiv.org/pdf/2004.07296.pdf (04/2004) Code : in paper
* Credible source: -

| autoencoder |  |
| --- | --- |
| - a type of neural networks that transforms input data into their output 
- uses two parts in this transformation
 * encoder : transforms its high dimensional inputs into a smaller set of dimensions while keeping the most important features
 * decoder : the reduced set of features is used to reconstruct the initial input data
- latent-space representation
 * the output of the encoder
 * a compressed form of the input data in which the most influential and important features are kept | ![evaluation-2](/assets/img/post/literature/cluster01.png){:width="40%" :.centered loading="lazy"} |

| training data | experiment | evaluation and output |
| --- | --- | --- |
| dataset 
* collect 70 compa nies listed by S&P 500 (h ttps://e n. wikipe dia. org /wiki /List_o f_S% 26P_5 00_co mpani es) 
* scrap the time series data using read_ html Python library 
* capture adjusted close price from yahoo (01 /Jan /2019 to 15 /Apr /2019) stock market data can be characterised| 
1. first step : using k-means clustering, cluster no label time series data, and keep the cluster as label
2. second step : using autoencoder based deep neural network, build prediction model
it models hidden features and takes into account such features into the prediction | The case study conducted in the context of the financial time series data shows t accuracy of %87.5 in clustering such data.
More importantly, we observed that the deep learning-based model outperforms t conventional K-Means clustering. |