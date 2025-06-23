## **Day 2 Reflection – [3 June 2025]**

### Theory sessions (Milan De Cauwer)
### **1. Key Ideas and Problems Discussed**
The materials used by the instructors are in the repo folder itself. In this section, I am going to list out some important concepts that were introduced and we will take a slight deeper dive in some topics i find challenging and write my own understanding of it.
#### When do linear classifiers work well?
Linear classifiers, like logistic regression or linear SVM, work well when the classes can be separated by a straight line (or a hyperplane in more than two dimensions). If the data has a mostly linear pattern and you do not need to capture complex interactions between features, a linear model can be both effective and interpretable. The best part is, they are fast, require less data to train, and are easier to understand.


#### Logistic regression and its loss function
Logistic regression is a go-to method for binary classification problems. It estimates the probability that a sample belongs to a particular class using a sigmoid function. Under the hood, it tries to find the best coefficients that minimize a function called log loss or cross-entropy loss. This loss function penalizes incorrect predictions more when the model is very confident and wrong. That’s a smart way of encouraging models not just to be right, but to be cautiously confident.
#### Decision Trees
A decision tree splits the data by asking a series of “yes or no” questions about the features. It keeps dividing the dataset based on the feature that best separates the classes, using a measure like Gini impurity or information gain. The tree continues to grow until it can’t improve much or reaches a stopping rule. Decision trees are great because they’re easy to visualize and explain, but they can overfit if they get too deep.


#### Random Forest
A random forest takes the idea of a decision tree and improves it by building not just one, but hundreds of them. Each tree sees a slightly different view of the data and uses a random subset of features. Then all their predictions are averaged (for regression) or voted (for classification). This usually gives better performance and stability, since the model is less likely to overfit to the noise in a single tree.
#### Evaluation metrics
Evaluating a model’s performance isn’t just about accuracy. Especially in imbalanced datasets, you want to know how well the model identifies true positives and avoids false alarms. Precision tells you how many of the positive predictions were actually correct. Recall tells you how many of the actual positives you caught. F1 score balances the two. These help you decide if your model is good enough for your goal — like catching diseases early or avoiding misclassifying healthy patients.


