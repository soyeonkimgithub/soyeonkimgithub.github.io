---
layout: post
title: Random Forests vs SVM 
categories: machinelearning
sitemap: false
hide_last_modified: true
published: true
---

## [ML] Random Forests vs SVM

### background

Both Random Forests (Decision Tree) and Support Vector Machine are supervised learning method used for classification and regression.

### description

- Random Forests
    - Tree-based methods are considered non-parametric, making no assumption on the distribution of data and the structure of the true model.
    - a way to improve performance of single decision tree, a new random sample of features is chosen for every single tree at every single split
- Support Vector Machine
    - aim of SVM is to find the best possible line (decision boundary) that separates the data points of different data classes.
    - this boundary is called a hyperplane when working in high-dimensional feature spaces.
    - The idea is to maximise the margin, which is the distance between the hyperplane and the closest data points of each category, thus making it easy to distinguish data classes.
    - SVM is useful for analysing complex data that cannot be separated by a simple straight line.
    - The key idea behind it is, to transform the input data into a higher-dimensional feature space using a kernel function.
    - Instead of explicitly calculating the coordinates of the transformed space, the kernel function enables the SVM to implicitly compute the dot products between the transformed feature vectors and avoid handling expensive, unnecessary computations for extreme cases.
- Random Forests
    - allow you to determine the feature importance, SVM cannot
    - much quicker and simpler to build
    - for multi-class classification problem, SVMs require a one-vs-rest method, which is less scalable and more memory intensive.

### how to use

- Random Forests
~~~python
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier

dtree = DecisionTreeClassifier()
dtree.fit(X_train, y_train)
pred = dtree.predict(X_test)

rf = RandomForestClassifier(n_estimators=100)
rf.fit(X_train, y_train)
rf_pred = rf.predict(X_test)
~~~

-SVM
~~~python
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier

dtree = DecisionTreeClassifier()
dtree.fit(X_train, y_train)
pred = dtree.predict(X_test)

rf = RandomForestClassifier(n_estimators=100)
rf.fit(X_train, y_train)
rf_pred = rf.predict(X_test)
~~~