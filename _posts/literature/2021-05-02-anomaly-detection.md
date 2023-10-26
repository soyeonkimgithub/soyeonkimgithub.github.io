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

## Detection of Accounting Anomalies in the Latent Space using Adversarial Autoencoder Neural Networks
* Goal : application of adversarial autoencoder networks that are capable of learning a semantic meaningful representation of real-world journal entries
* Link : https://arxiv.org/pdf/1908.00734.pdf (08/2019)
* Code : https://github.com/GitiHubi/deepAD
* Credible source: 2nd KDD Workshop on Anomaly Detection in Finance


| training data | method | output |
| --- | --- | --- |
| 1. real-world journal entries from SAP ERP system
2. synthetic dataset
a. data A - is an extract of
an SAP ERP and encompasses the entire population of journal entries of a single fiscal year
b. data B - is an excerpt of the synthetic dataset presented in https://www.kaggle.com/ntnu- testimon/paysim1
c. pre-process the categorical entry to obtain a binary ("one- hot" encoded) representation by using pandas. get_dummies(), and numerical entry to be normalised
d. we inject a small fraction of synthetic global and local anomalies into both datasets.
one-hot encoding : each categorical level becomes a separate feature in the dataset containing binary values (1 or 0). | Adversarial Autoencoder Neural Networks extends the concept of Autoencoder Neural Networks (AE) by imposing an arbitrary prior on the AEs latent space using a GAN training setup | global and local anomalies
global accounting anomalies are journal entries that exhibit unusual or rare individual attribute values. Such anomalies usually relate to skewed attributes, e.g., rarely used ledgers, or unusual posting times.
local accounting anomalies are journal entries that exhibit an unusual or rare combination of attribute values while their individual attribute values occur quite frequently, e.g., unusual combinations of general ledger accounts or user accounts used by several accounting departments. | 



| training data | method | output |
| --- | --- | --- |
| 1. real-world journal entries from SAP ERP system
2. synthetic dataset
a. data A - is an extract of
an SAP ERP and encompasses the entire population of journal entries of a single fiscal year
b. data B - is an excerpt of the synthetic dataset presented in https://www.kaggle.com/ntnu- testimon/paysim1
c. pre-process the categorical entry to obtain a binary ("one- hot" encoded) representation by using pandas. get_dummies(), and numerical entry to be normalised
d. we inject a small fraction of synthetic global and local anomalies into both datasets.
one-hot encoding : each categorical level becomes a separate feature in the dataset containing binary values (1 or 0). | Adversarial Autoencoder Neural Networks
extends the concept of Autoencoder Neural Networks (AE) by imposing an arbitrary prior on the AEs latent space using a GAN training setup | global and local anomalies
global accounting anomalies are journal entries that exhibit unusual or rare individual attribute values. Such anomalies usually relate to skewed attributes, e.g., rarely used ledgers, or unusual posting times.
local accounting anomalies are journal entries that exhibit an unusual or rare combination of attribute values while their individual attribute values occur quite frequently, e.g., unusual combinations of general ledger accounts or user accounts used by several accounting departments. | 

