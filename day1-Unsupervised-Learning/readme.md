## Table of Contents

- [Day 1 Reflection – 2 June 2025](#day-1-reflection--2-june-2025)
  - [Theory Sessions (Katarzyna Michałowska)](#theory-sessions-katarzyna-michałowska)
    - [1. Key Ideas and Problems Discussed](#1-key-ideas-and-problems-discussed)
      - [Unsupervised Learning 101](#unsupervised-learning-101)
        - [Multivariate Similarity](#multivariate-similarity)
        - [Elbow Method](#elbow-method)
        - [Hierarchical Clustering](#hierarchical-clustering)
        - [DBSCAN: Density-Based Clustering](#dbscan-density-based-clustering)
        - [Dimensionality Reduction](#dimensionality-reduction)
          - [PCA](#pca)
          - [t-SNE](#t-sne)
          - [Auto-encoders](#auto-encoders)
          - [UMAP](#umap)
  - [Hands-on Sessions (Katarzyna Michałowska and Pubudu)](#hands-on-sessions-katarzyna-michałowska-and-pubudu)
    - [The Problem](#the-problem)
    - [The Solution](#the-solution)
      - [Data Preparation](#data-preparation)
      - [PCA Implementation](#pca-implementation)
        - [How Many Components to Keep?](#how-many-components-to-keep)
        - [What Do These Components Mean?](#what-do-these-components-mean)
      - [K-means Cluster Analysis](#k-means-cluster-analysis)
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
When we work with data that has many features, such as thousands of genes or pixels, it becomes difficult to visualize and even harder to understand. Not all features are equally important, and some might even repeat similar information. Dimensionality reduction helps by reducing the number of features while keeping the most important parts of the data. You can think of it as shrinking a large and complicated dataset into a simpler version that still holds the main message. This not only makes it easier to visualize but also helps models perform better by removing unnecessary noise. Here, I am going to simply describe some techniques of dimensionality reduction without going into too much detail or maths. But I'll keep these topics to write more detailed articles as I find them super interesting. 
##### PCA
PCA is like finding the best angle to look at your data from. It rotates your data into a new set of axes called principal components, which are just combinations of your original features. The first one captures the most variation, the second one captures the next most, and so on. You can then keep just the top few components and ignore the rest. It is fast, linear, and great for getting a rough sense of structure.

##### t-SNE
t-SNE is more about preserving relationships between individual points than summarizing global structure. It is especially good at showing how points form clusters. If two data points are similar, t-SNE makes sure they end up close together in 2D or 3D. It is perfect for visualizing high-dimensional data but not great for downstream analysis because the axes don’t mean anything. You just look at the patterns.

##### Auto-encoders
Autoencoders are a type of neural network that learns to compress data into a smaller hidden version of itself, and then reconstruct it back again. If it can recreate the input well using only this hidden smaller version, that smaller version must be capturing the most important features. Autoencoders are powerful because they can learn complex, non-linear patterns that simple methods like PCA can miss.


##### U-map
UMAP is like a mix of the best parts of t-SNE and PCA. It preserves both local neighborhoods and global structure better than t-SNE, and it is faster too. You can use it to visualize how samples are related to each other in a way that feels natural. It is great for spotting patterns or groups in your data, especially when you do not know what to expect.

### Hands-on  sessions (Katarzyna Michałowska and Pubudu)
We are not going to discuss the nitty gritty of the hands on session here. You can check out the notebook `1.Notebook_PCA_n_Clustering_session.ipynb`. It is well documented, anyone can follow along easily. 

What we are going to discuss here is the approach taken to solve the particular problem and why it makes sense and take a high level view of the whole thing. 

### The Problem
We were given a dataset that contained information on 25 patients and how they responded to 50 different drug compounds. Each patient had a measurement for every drug, which told us how sensitive they were to that particular compound.

At first glance, this might look like a straightforward dataset, but it actually presents a classic case of what is known as high dimensional data. In other words, there are more features or measurements per patient than there are actual patients. This creates several challenges when it comes to analysis.

The first issue is about visualization. We are used to thinking in two or three dimensions because that is what we can easily plot and interpret. But once we have 50 features, we can no longer picture the relationships in our heads or on a simple chart. So if we want to find patterns in how different patients respond to the drugs, we need to somehow reduce that complexity.

The second challenge is more subtle. In high dimensional spaces, the idea of distance becomes less reliable. Normally, we might use distance between points to say how similar or different two patients are. But in this case, because everything is spread out across so many dimensions, the nearest and farthest points start to feel equally far away. That makes methods like clustering or nearest neighbor searches much less meaningful.

Another important concern is overfitting. When a dataset has more features than examples, there is a higher risk that a model might fit the noise rather than the signal. It can pick up patterns that are not actually meaningful, which leads to poor generalization when the model is tested on new data.

So our goal in this case was to simplify the dataset while still keeping the important information. We needed to find a way to reduce the number of features in a smart way, so that we could better explore how patients responded to the drugs, look for similarities, and potentially discover useful biological insights.
### The Solution
#### Data prepararion
Before we begin applying transformation to the data, we need to make sure the data is clean and consistent. That means checking for any missing values, separating the actual drug sensitivity features from metadata like patient IDs, and looking for outliers or odd patterns. Since the values come from different drugs and may have different ranges, we also scale the data so that everything is on the same playing field. This is especially important because later steps, like PCA, are very sensitive to differences in scale. The idea is to give every feature a fair chance to contribute.

#### PCA implementation
Once the data was cleaned and scaled, the next step was to make sense of its complexity. PCA, or Principal Component Analysis, was the method used here. The idea behind PCA is to take the original features and find new ones that summarize most of the important variation in the data, but with fewer dimensions.

The algorithm first figures out which directions in the data carry the most variation. These directions are called principal components. The data is then projected onto them, giving us a new set of features that are uncorrelated with each other. This helps remove redundancy and makes patterns easier to spot.

Since we had only 25 patients, PCA could extract at most 25 components. We looked at how much variance each component explained and picked the top ones that captured most of the information. This way, we could shrink the data while keeping the key structure intact.

##### How Many Components to Keep?
Once PCA gives us all the components, the next question is how many of them we should actually keep. We used a few strategies to answer that.

First, we looked at how much variance each component explains. This tells us how much information from the original data is being captured. By adding up the variance from the top components, we can see how much of the overall structure we’re preserving. For example, the first few components might already capture more than 90 percent of the total variance, which is often good enough.

One method is to use a variance threshold. Here, we simply choose enough components to explain a fixed amount of the variance, like 90 or 95 percent. Another method is to look at a scree plot, which shows the variance explained by each component. When the curve starts to flatten out, that point is called the "elbow" and often marks a good stopping point. Beyond that, extra components add very little new information.

We also used a built-in PCA option that automatically picks the smallest number of components that meet a chosen variance target. This is a simple way to make the choice more systematic and reproducible.

##### What Do These Components Mean?
To make sense of the new components, we examined the feature loadings. These are the weights that tell us how much each original feature contributes to each principal component. A high loading (positive or negative) means that feature strongly influences that component.

By looking at which features had the highest loadings, we got a sense of what each component was capturing. For example, if a component was driven mostly by a few specific drugs, we could interpret it as a pattern related to those compounds’ effects. This helps connect the reduced data back to the biology or experimental context it came from.

This whole process of dimensionality reduction and interpretation made it easier to see structure in the data, reduced noise, and set us up for better downstream analysis.

#### K-means Cluster Analysis
Once we reduced our dataset into a smaller number of meaningful dimensions using PCA, the next step was to uncover hidden structure within that data. This is where clustering comes in, and we started with one of the most popular methods: K-means clustering.

At its core, K-means tries to group samples such that each one is as close as possible to the "center" of its assigned cluster. That center is just the average of all points in the cluster. The algorithm works by guessing where those centers should be, checking how far each point is from those centers, moving the centers based on where the points ended up, and repeating this until everything stabilizes.

To figure out how good our clustering is, we used two metrics. The first is inertia, which just measures how tightly packed each cluster is. Lower inertia is better, but it always goes down if we keep adding more clusters. That is why we use something called the elbow method, where we look for the point where adding more clusters stops helping much. 

The second metric is the silhouette score, which tells us not only how close each point is to its own cluster but also how far it is from other clusters. A high score means the clusters are well separated and the points are nicely grouped.
We tried several values of K and plotted both metrics. Based on where the silhouette score peaked and where the inertia curve leveled off, we chose K = 3 as the optimal number of clusters.

After that, we fit the K-means model using this optimal K and assigned each patient to one of the three clusters. We then looked at the cluster centers in PCA space to see what made each group distinct. Cluster 0, for example, had high values on the first principal component, while Cluster 2 had very low values. This suggests the traits captured by that component play a key role in separating the groups.

Finally, we visualized the clusters using the first two principal components and labeled each patient. This made it easier to spot patterns and also gave us some insight into how distinct or overlapping the clusters really are.

In short, K-means helped us take a high-dimensional dataset, simplify it with PCA, and then reveal patient subgroups that might respond differently to drugs or have other biological similarities worth investigating.
