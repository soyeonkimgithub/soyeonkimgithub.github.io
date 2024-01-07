---
layout: post
title: Decision Tree and Random Forest
categories: dsa
sitemap: false
hide_last_modified: true
published: true
---
## [Algorithm] Decision Tree and Random Forest

### Decision Tree and Random Forest
* Entropy and Information Gain are the mathematical methods of choosing the best split
* best split → trying to maximise your information gain of this split
* problem of decision tree : high variance (low accuracy)
* bagging is a procedure for reducing the variance of ML method
* bootstrap samples of training set means sampling from the training set with replacement
* random forests → a way to improve performance of single decision tree, a new random sample of features is chosen for every single tree at every single split, decorrelated the trees
* there is one very strong feature, when using ‘bagged’ trees, most of the trees will use that feature as the top split, resulting in an ensemble of similar trees that are highly correlated → which is avoid because averaging highly correlated quantities does not significantly reduce variance

~~~python
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import confusion_matrix, classification_report

dtree = DecisionTreeClassifier()
dtree.fit(X_train, y_train)
pred = dtree.predict(X_test)
print(confusion_matrix(y_test, pred))
print(classification_report(y_test, pred))

rf = RandomForestClassifier(n_estimators=100)
rf.fit(X_train, y_train)
rf_pred = rf.predict(X_test)
print(confusion_matrix(y_test, rf_pred))
print(classification_report(y_test, rf_pred))
~~~