## **Day 1 Reflection – [2 June 2025]**

### Theory sessions (Katarzyna Michałowska)
### **1. Key Ideas and Problems Discussed**
The materials used by the instructors are in the repo folder itself. In this section, I am going to list out some important concepts that were introduced and we will take a slight deeper dive in some topics i find challenging and write my own understanding of it.

**Unsupervised Learning 101**
`Learning by observation` that is to learn patterns among the data is the nutshell of unsupervised learning. 

  #### Multivariate similarity:
Let's talk about multivariate similarity. As the name suggests, it is about measuring how similar different samples are when each sample has more than one feature. For example, imagine you have patients, and for each patient, you have thousands of gene expression values. Each of those features becomes a separate dimension in space, and each patient becomes a point in that high-dimensional space.

The goal is to measure how close or far apart those points are. If two patients have similar gene expression patterns, they will be closer together. If they are very different, they will be farther apart. To calculate this, we use distance metrics. One common method is Euclidean distance, which is the straight-line distance you learned in geometry. It calculates how far two points are based on their feature values. Another method is correlation distance, which focuses not on the absolute values but on the pattern or trend across features. If two samples increase and decrease in similar ways across features, even with different values, they may still be highly correlated.

Scaling the features is very important here. If one feature has a much larger numerical range than the others, it can dominate the distance calculation. Scaling ensures that each feature contributes equally to the result.

We cannot visualize spaces with hundreds or thousands of dimensions. Our naive brains are not built for that. But computers can handle this high-dimensional data. Later we will look at how to reduce these dimensions in a way that keeps the important structure intact so that we can interpret the data meaningfully.


#### Elbow Method
Let’s say we want to divide data into clusters, but we do not know how many clusters we should aim for. The Elbow Method helps us find a good number. We try clustering the data with different numbers of clusters and then calculate a score called “within-cluster sum of squares” which tells us how tightly grouped the points in each cluster are. As we increase the number of clusters, this score gets better. But after a certain point, the improvement becomes very small. That turning point looks like an elbow when you plot it. That is where we stop, because adding more clusters after that does not really give us better grouping.

#### Hierarchihcal clustering
This is a way of clustering that builds a tree of clusters. At first, we treat every data point as its own cluster. Then we start merging the closest ones, step by step, until everything becomes one big cluster. What is cool about this method is that it creates a hierarchy. You can actually choose your level of grouping by cutting the tree at different heights. It is especially useful when you want to see nested structures in your data, like subtypes within a cancer type.

#### DBSCAN: Density-Based Clustering
Unlike methods that assume clusters are round or evenly sized, DBSCAN is based on how dense the data is in a region. If a point has a lot of neighbors around it, it belongs to a cluster. If it is in a sparse region, it gets labeled as noise. This is useful when clusters are oddly shaped or when you want to find outliers. It does not need you to say how many clusters to look for, which is nice when that number is not obvious.

#### Dimensionality reduction
##### PCA
##### t-SNE
##### Auto-encoders
##### U-map

### Hands-on  sessions (Katarzyna Michałowska and Pubudu)
### **2. Algorithm/Method Applied**
Which method was discussed and why was it suitable?

### **3. “Problem-to-Solution” Thought Process**
How was the problem framed and how did the ML method solve it?

### **4. Personal Takeaways**
What did I learn?



