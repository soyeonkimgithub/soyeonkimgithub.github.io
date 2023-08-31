---
layout: post
title: Principal Component Analysis
categories: study
sitemap: false
hide_last_modified: true
published: true

---
## [Algorithm] Principal Component Analysis

### Principal Component Analysis
* PCA is just a transformation of your data and it attempts to find out what feateures explain the most variance in your data.
* PCA plot converts the correlations among all of the variables into a 2-D graph.
* The axes are ranked in order of importance.
* dimension reduction, general factor analysis
* PCA can tell us which variable is the most valuable for clustering the data. (i.e. PCA might tell us that variable 3 is responsible for separating samples along the x-axis.)
* PCA can tell us how accurate the 2-D graph is.
* PC1 is largest sum of the squared distances between the projected points and the origin.

* For a large number of variables, we can compress the amount of explained variation to just a few components.
* Unsupervised statistical technique used to examine the interrelations among a set of variables in order to identify the underlying structure of those variables. 
* where regression determines a line of best fit to a data set, factor analysis determines several orthogonal lines of best fit to the data set
* orthogonal → at right angles (lines are perpendicular to each other in n-dimensional space)
* n-dimensional space is the variable sample space. (in the data set with 4 variables the sample space is 4-dimensional) 


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


