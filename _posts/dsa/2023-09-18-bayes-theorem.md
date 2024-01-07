---
layout: post
title: DSA 
categories: dsa
sitemap: false
hide_last_modified: true
published: true
---

## [Algorithm] Bayes' Theorem

### description

- conditional probability
- find the probability of an event, based on prior knowledge of conditions that might be related to that event.
- determine the conditional probability of event A when event B has already happened.
- “The conditional probability of an event A, given the occurrence of another event B, is equal to the product of the event of B, given A and the probability of A divided by the probability of event B.”
- P(A|B) = P(B|A)P(A) / P(B)

### how to use

- if the risk of developing health problems is known to increase with age, Bayes’ Theorem allows the risk to an individual of a known age to be assessed more accurately (by conditioning it on his age) than simply assuming that the individual is typical of the population as a whole.
- Assume the incidence rate of pancreatic cancer is 1/100,000, while 1/10,000 healthy individuals have the same symptoms, the probability of having pancreatic cancer given the symptoms is 9.1%

### Naive Bayes

- Naive Bayes classifiers are a collection of classification algorithms based on Bayes’ Theorem.
- The fundamental Naive Bayes assumption is that each feature makes an independent and equal
    - assume that no pair of features are dependent. i.e. the temperature being ‘hot’ has nothing to do with the humidity or the outlook being ‘rainy’ has no effect on the winds.
    - each feature is given the same weight. i.e. knowing only temperature and humidity alone cannot predict the outcome accurately. none of the attributes is irrelevant and assumed to be contributing equally to the outcome.
- not generally correct in real-world. the independence assumption is never correct but often works well in practice.