---
layout: post
title: Anomaly Detection
categories: literature
sitemap: false
hide_last_modified: true
published: true
---
## [ML] Anomaly Detection

## A Unifying Review of Deep and Shallow Anomaly Detection
* Goal : identify the common underlying principles as well as the assumptions that are often made implicitly by various methods 
* Link : https://research.google/pubs/pub50044/ (05/2021)
* Code : -
* Credible source: Google Research

### Background knowledge
* anomaly : an anomaly is an observation that deviates considerably from some concept of normality 
* type of anomalies 
    1.	point anomaly : an individual anomalous data point
    - i.e. illegal transaction in fraud detection or image of a damaged product in manufacturing
    2.	conditional or contextual anomaly : anomalous data in a specific context such as time, space or the connections in a graph
    - i.e. price of $1 Apple stock might be normal back then, mean daily temperature below freezing point would be anomaly in Amazon,
    - add contextual variable T in equation
    3.	group or collective anomaly : set of related or dependent points that is anomalous
    - i.e. cluster of anomalies such as similar or related network attacks

* types of machine learning approaches for anomaly detection (shallow and deep learning anomaly detection) are usually referred to as low and high, which is the level in the feature hierarchy of some hierarchical distribution 
    1.  low-level / sensory anomalies 
    - semantic concepts: individual characters and 
    - words pixel-level features: edges or texture
    2.  high-level / semantic anomalies 
    - semantic concepts: topics 
    - pixel-level features: objects and scenes in image

* anomaly, outlier, and novelty
    - anomalies are often the data points of interest (e.g., a longterm survivor of a disease) outliers are frequently regarded as ‘noise’ or
    - ‘measurement error’ that should be removed in a data preprocessing step (‘outlier removal’) 
    - novelties are new observations that require models to be updated to the ‘new normal’
* challenges in anomaly detection
    - mostly unsupervised nature of the problem
* different approaches    
    - typical decision functions 
        * one-class classification model : learn a discriminative decision boundary 
        * probabilistic model : learn density
        * reconstruction model : learn some underlying geometric structure of the data 
    - shallow and deep feature maps 
        * one-class classification model : SVDD, Deep SVDD 
        * probabilistic model : KDE, Flows 
        * reconstruction model : PCA, AE

*  probability density estimation (https://machinelearningmastery.com/probability-density-estimation/)
    1.	the relationship between observations and their probability
    2.	useful to know the probability density function for a sample of data in order to know whether a given observation is very unlikely as to be considered an anomaly
    3.	parametric probability density estimation : involves selecting a common distribution (uniform, normal, exponential) and estimating the parameters for the density function from a data sample
    4.	nonparametric probability density estimation : involves using a technique to fit a model to the arbitrary distribution of the data, like kernel density estimation
        a.	still have parameters but not directly controllable in the same way as simple probability distributions
        b.	i.e. using all observations in a random sample, in effect making all observations in the sample "parameters"

### Model