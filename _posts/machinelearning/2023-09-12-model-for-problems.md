---
layout: post
title: Model for Problems
categories: machinelearning
sitemap: false
hide_last_modified: true
published: true
---
## [ML] Model for Problems

### background

- supervised: human builds model based on input/output
- unsupervised: human input, machine output human utilises if satisfactory
- reinforcement: human input, machine output human reward/punish, cycle continues

### description

- Regression
    - Linear: numeric data
        
        *→ linear_model.LinearRegression()*
        
    - Logistic: target variable is categorical
        
        *→ linear_model.LogisticRegression()*
        
- Clustering
    - k-Means: similar datum into groups based on centroids
        
        *→ cluster.KMeans()*
        
    - Anomaly Detection: finding outliers through grouping
        
        *→ covariance.EllipticalEnvelope()*
        
- Classification
    - Neural Net: complex relationships, prone to overfitting, basically magic
        
        *→ neural_network.MLPClassifier()*
        
    - KNN: group membership based on proximity
        
        *→ neighbors.KNeighborsClassifier()*
        
    - Decision Tree: if/then/else, non-contiguous data, can also be regression
        
        *→ tree.DecisionTreeClassifier()*
        
    - Random Forest: find best split randomly, can also be regression
        
        *→ ensemble.RandomForestClassifier()*
        
    - SVM: maximum margin classifier, fundamental data science algorithm
        
        *→ svm.SVC(), svm.LinearSVC()*
        
    - Naive Bayes: updating knowledge step by step with new info
        
        *→ GaussianNB(), MultinominalNB(), BernouliNB()*
        
- Feature Reduction
    - tSNE (T-Distribution Stochastic Neighbour Embedding) → *manifold.TSNE()*
    - PCS (Principle Component Analysis) → *decomposition.PCA()*
    - CCA (Canonical Correlation Analysis) → *decomposition.CCA()*
    - LDA (Linear Discriminant Analysis) → *lda.LDA()*
- Other Concepts
    - Bias Variance Tradeoff
    - Underfitting/Overfitting
    - Inertia
    - Accuracy Function → *(TP+TN) / (P+N)*
    - Precision Function → *manifold.TSNE()*
    - Specificity Function → *TN / (FP+TN)*
    - Sensitivity Function → *TP / (TP+FN)*