---
layout: post
title: Dimension Reduction and PCA 
categories: machinelearning
sitemap: false
hide_last_modified: true
published: true
---

## [ML] Dimension Reduction and PCA

### background

Dimensionality reduction is the process of reducing the number of features (or dimensions) in a dataset while retaining as much information as possible. This can be done for a variety of reasons 1) to reduce the complexity of a model 2) to improve the performance of a learning algorithm 3) to make it easier to visualise the data.

### description

- high-dimensional data
    
    → a large number of features
    
    → model complexity increases (distance between data points getting huge)
    
    → overfitting
    
- Feature Selection → filter methods, wrapper methods, embedded methods
- Feature Extraction → creating new features by combining or transforming the original features to create a set of features that captures the essence of the original data in a lower-dimensional space
    - PCA (Principal Component Analysis)
        - dimensionality reduction method, used to reduce the dimensionality of large data sets by transforming a large set of variables into a smaller one that still contains most of the information in the large set
        - projects the original features onto a lower dimensional space while preserving as much of the variance as possible
        - principal components are new variables that are constructed as linear combination or mixtures of the initial features.
        - these combinations are done in such a way that the new variables are uncorrelated and most of the information within the initial variables is squeezed or compressed into the first components.
        - So, the idea is 10-dimensional data gives you 10 principal components but PCA tries to put maximum possible information in the first component then maximum remaining information in the second and so on.
    - LDA (Linear Discriminant Analysis)
    - t-SNE (t-distributed Stochastic Neighbour Embedding)

### how to use
~~~python
from sklearn.preprocessing import StandardScaler
from sklearn.decomposition import PCA

scaler = StandardScaler()
scaler.fit(df)
scaled_data = scaler.transform(df)

pca = PCA(n_components=2)
pca.fit(scaled_data)
x_pca = pca.transform(scaled_data)

plt.figure(figsize=(8,6))
plt.scatter(x_pca[:,0], x_pca[:,1],c=cancer['target'],cmap='plasma')
plt.xlabel('First Principal Component')
plt.ylabel('Second Principal Component')

df_comp = pd.DataFrame(pca.components_, columns=cancer['feature_names'])
plt.figure(figsize=(12, 6))
sns.heatmap(df_comp, cmap='plasma')
~~~