# BioNT-Applied Machine Learning for Biological Data Workshop Reflection and Notebooks-2025
[Details about the workshop](https://www.cecam.org/workshop-details/applied-machine-learning-for-biological-data-1459)
This was 5-day-long intensive workshop instructed by top professionals in their fields and organised by BioNT (Bio Network for Training) and co-organised by NAIC - Norwegian AI Cloud and @Centre Européen de Calcul Atomique et Moléculaire.. 


This repository is the collection of my reflections, notes, and code from the BioNT Workshop on **Applied Machine Learning for Biological Data**, held from **2–6 June 2025**.

This repository contains well-documented hands-on notebooks, presentations by instructors, my write-ups on core ML and bioinformatics concepts discussed throughout the sessions, and a deep dive into the applications of machine learning in genomics, clustering, classification, deep learning, and accelerated variant calling using NVIDIA GPUs.

---

## Table of Contents

- [Day 1 – Unsupervised Learning: PCA, Clustering](#day-1--unsupervised-learning-pca-clustering)
- [Day 2 – Classification and Regression](#day-2--classification-and-regression)
- [Day 3 – Model Validation and Optimisation](#day-3--model-validation-and-optimisation)
- [Day 4 – Deep Learning and DeepVariant](#day-4--deep-learning-and-deepvariant)
- [Day 5 – Accelerated Genomics with Parabricks](#day-5--accelerated-genomics-with-parabricks)
- [Assignment Notebook](#assignment)
- [Resources and Notebooks](#resources-and-notebooks)
- [Acknowledgment](#acknowledgment)

---

## Day 1 – [Unsupervised Learning: PCA, Clustering](./day1-Unsupervised-Learning/readme.md)

Learned how to handle high-dimensional biological data using:
- PCA for dimensionality reduction
- k-means and hierarchical clustering
- Distance metrics and similarity
- t-SNE, Autoencoders

---

## Day 2 – [Classification and Regression](./day2-Classification&Regression/readme.md)

Explored:
- Logistic regression, Decision Trees, Random Forests
- Model evaluation (precision, recall, F1)
- Linear and non-linear regression
- Loss functions and regularization

---

## Day 3 – [Model Validation and Optimisation](./day3-ModelValidation&Optimisation/readme.md)

Covered:
- Overfitting and bias-variance tradeoff
- Data leakage and splitting
- Grid search vs. random search
- Evaluation baselines and robustness

---

## Day 4 – [Deep Learning and DeepVariant](./day4-Deeplearning&DeepVariant/readme.md)

Covered fundamentals of neural networks:
- Shallow and deep networks
- Activation functions and backpropagation
- Cross-entropy loss and max likelihood
- DeepVariant for GPU-accelerated variant calling

---

## Day 5 – [Accelerated Genomics with Parabricks](./day5-Acclerated-genomics-Parabricks/readme.md)

Worked with:
- Containers and NVIDIA GPUs
- Running genomics workflows with Parabricks
- FASTQ to BAM pipeline and variant calling with DeepVariant

---

## Assignment

The complete assignment extension from Day 3's logistic regression notebook:
-  [`assignment_2panad.ipynb`](./assignment_2panad.ipynb)

Includes:
- Model comparison (LogReg, Random Forest, SVM, k-NN)
- Hyperparameter tuning with GridSearchCV
- Evaluation metrics and visualization
- Summary plots

---

## Resources and Notebooks

All workshop notebooks and datasets are inside the corresponding day folders. You can explore:

- Clean and reproducible Jupyter notebooks
- Personal markdown notes 

Some other relevant links:
- [Workshop Hands-on rendered page](https://naicno.github.io/BioNT_Module2_handson/#)
- [Accelerated Genomics rendered page](https://coderefinery.github.io/BioNT_Lesson_Accelerated_Genomics/#)
- [GPU and parallel processing rendered page](https://training.pages.sigma2.no/tutorials/gpu-intro/index.html)
- [Workshop interaction page where participants aksed the questions and instructors answerd](https://biont.biobyte.de/VPI_52LLQCmp_P4QYFhFXg?view)
---
## Acknowledgment
This workshop was organized by  **BioNT** and hosted at the **University of Oslo (UiO)**. Huge thanks to:

- **Katarzyna Michałowska**, SINTEF Norway  
- **Milan De Cauwer**, SINTEF Norway  
- **Elias Myklebust**, Simula Research Laboratory  
- **Pubudu Saneth Samarakoon**, University of Oslo
- **Sabry Razick**, University of Oslo

Special shoutout to all the teaching assistants and organizers who made sure we had working environments, clean data, and functional GPUs.

---

**Author:**  
Amar Khatri   
If you want to get in touch or discuss anything from the repo, feel free to [connect on LinkedIn](https://www.linkedin.com/in/amarkhatri/)





