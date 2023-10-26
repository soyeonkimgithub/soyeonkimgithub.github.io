---
layout: post
title: Kernel Trick
categories: machinelearning
sitemap: false
hide_last_modified: true
published: true
---

## [ML] Kernel Trick

### background

- when there are more and more dimensions, computations within that space become more and more expensive. this is when the kernel trick comes in. it allows us to operate in the original feature space without computing the coordinates of the data in a higher dimensional space.
- kernels, (kernel techniques or kernel functions) are a collection of distinct forms of pattern analysis algorithms, using a linear classifier. It solves an existing non-linear problem. SVM uses kernels methods to solve classification and regression issues.

### description

- is a simple method where a non linear data is projected onto a higher dimension space so as to make it easier to classify the data where it could be linearly divided by a plane.
- choose the right kernel function is important otherwise, we may overfit the model when we map data to a higher dimension.

### how to use

- SVM → bridge linearity and non-linearity