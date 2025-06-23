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

#### Hierarchihcal clustering

#### DBSCAN: Density-Based Clustering

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



