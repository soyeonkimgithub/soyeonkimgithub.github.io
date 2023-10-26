---
layout: post
title: KNN and k-Means
categories: machinelearning
sitemap: false
hide_last_modified: true
published: true
---
## [ML] KNN and k-Means

### background

KNN is a supervised learning algorithm mainly used for classification problem, while k-Means is unsupervised learning algorithm.

### description

- KNN (K: number of nearest neighbours)
    - calculate the distance from new data(x) to all points
    - sort the points by increasing distance from x
    - predict the majority label of the ‘k’ closest points
- k-means (k: number of clusters)
    - choose a number of clusters ‘k’
    - randomly assign each point to a cluster
    - until clusters stop changing,
        - keep compute the cluster centroid by taking the means vector of points in the cluster
        - assign each data point to the cluster for which the centroid is the closest
    - elbow method can be used to select k
        - compute the sum of squared error for each number of k
        - when the number of clusters increase, error should be smaller
        - choose the k at which the error decrease abruptly (elbow point)
    - pros : simple to understand, fast to cluster, easy to implement
    - cons : need to pick the right ‘k’, sensitive to initialisation, sensitive to outlier, spherical solutions, need standardisation

### how to use

- KNN
~~~python    
    from sklearn.neighbors import KNeighborsClassifier
    knn = KNeighborsClassifier(n_neighbors=1)
~~~

- k-Means
~~~python
    from sklearn.cluster import KMeans
    kmeans = KMeans(n_clusters=2)
~~~    
