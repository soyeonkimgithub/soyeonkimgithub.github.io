---
layout: post
title: K Means Clustering
categories: study
sitemap: false
hide_last_modified: true
published: true
---
## [Algorithm] K Means Clustering

### K Means Clustering
* allow us to cluster unlabelled data → unsupervised learning algorithm
* attempt to group similar clusters together (i.e. cluster similar documents, cluster customers based on features, market segmentation, identify similar physical groups)
* algorithm
1. choose a number of clusters ‘k’ → elbow method
2. randomly assign each point to a cluster
3. until clusters stop changing, 
    a. for each cluster, compute the cluster centroid by taking the mean vector of points in the cluster
    b. assign each data point to the cluster for which the centroid is the closes
* elbow method
1. compute the SSE(sum of squared error) for some values of k
2. SSE is defined as the sum of the squared distance between each member of the cluster and its centroid
3. when the number of clusters increase, error should be smaller
4. choose the k at which the SSE decreases abruptly

~~~python
from sklearn.cluster import KMeans

kmeans = KMeans(n_clusters=2)
kmeans.fit(data.drop('Private', axis=1))
kmeans.cluster_centers_
kmeans.labels_
~~~