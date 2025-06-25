## **Day 2 Reflection – [3 June 2025]**
## Table of Contents

- [Theory Sessions (Milan De Cauwer)](#theory-sessions-milan-de-cauwer)
  - [1. Key Ideas and Problems Discussed – Classification](#1-key-ideas-and-problems-discussed--classification)
    - [When Do Linear Classifiers Work Well?](#when-do-linear-classifiers-work-well)
    - [Logistic Regression and Its Loss Function](#logistic-regression-and-its-loss-function)
    - [Decision Trees](#decision-trees)
    - [Random Forest](#random-forest)
    - [Evaluation Metrics](#evaluation-metrics)
  - [2. Key Ideas and Problems Discussed – Regression](#2-key-ideas-and-problems-discussed--regression)
    - [How Does Linear Regression Work?](#how-does-linear-regression-work)
    - [From Linear to Nonlinear Models](#from-linear-to-nonlinear-models)
    - [Minimizing the Loss Function](#minimizing-the-loss-function)
    - [Gradient Descent Optimization](#gradient-descent-optimization)
    - [What Model Should I Choose?](#what-model-should-i-choose)
    - [How to Evaluate a Regressor](#how-to-evaluate-a-regressor)
    - [Overfitting and Regularization](#overfitting-and-regularization)
- [Hands-on Session (Milan De Cauwer and Pubudu)](#hands-on-session-milan-de-cauwer-and-pubudu)

---
### Theory sessions (Milan De Cauwer)
### **1. Key Ideas and Problems Discussed/ Classification**
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

### **Regression**

#### How does linear regression work?
Linear regression is a way to describe the relationship between an input and an output using a straight line. The goal is to find the best line that captures the pattern in the data. For example, if you have house size and price, linear regression tries to draw a line that best predicts price based on size. We do this by adjusting the slope and the intercept of the line until the distance between the actual data points and the predicted values is as small as possible. These distances are squared and summed to form a loss function, and the model tries to minimize it. In simple terms, we are tuning the line to fit the data as closely as we can.

#### From Linear Models to Nonlinear Models
Sometimes, a straight line is not good enough. The relationship between inputs and outputs can be curved, irregular, or have sudden jumps. In those cases, linear regression falls short.

But the underlying idea remains the same. We are still trying to find a function that fits the data by minimizing a loss. The only difference is that now we may choose a more flexible function like a curve or even use techniques that can adapt to more complex shapes. This shift opens the door to many types of models, including polynomial regression or neural networks.
#### Minimizing the Loss Function
Regardless of the model, the idea of minimizing a loss function is at the heart of regression. We want our predictions to be close to the real values, and the loss function gives us a way to measure that closeness.

For simple models, we can find the minimum using algebra. For more complex ones, we often use iterative techniques like gradient descent. Think of gradient descent as standing on a hill and walking downhill by always stepping in the direction that lowers your altitude the fastest. Eventually, if you are careful, you reach the bottom, which represents the best fit.

#### Optimizing Your Loss Function via Gradient Descent
Gradient descent is a powerful and widely used method for training models, especially when the math gets too messy for direct solutions. It works by starting with a random guess for the model’s parameters, checking how bad the predictions are, and then adjusting the parameters to reduce the error.

You repeat this process over and over until the model settles into a good solution. It does not always find the absolute best answer, but with good settings and clean data, it usually gets close enough to be useful.
#### Regression – What model should I choose?
Choosing the right regression model depends on what your data looks like and what kind of relationship you expect between inputs and outputs.If the relationship looks straight and consistent, a simple linear model might be perfect. If the relationship curves or twists, you might need polynomial regression or something more flexible. And if things get really complicated, neural networks or ensemble methods might be the way to go.

It is also a balance between complexity and generalization. Simpler models are easier to understand and often generalize better, while complex models can fit the data more closely but might also capture noise. Thinking about what you want to achieve and how much you trust your data can help guide your choice.
#### How do I evaluate a regressor?
Once your model is trained, you need to check how good it is. The most common way is by using metrics that compare predicted values to actual ones.

R-squared tells you how much of the variation in the output is explained by your model. A value close to one means your model is doing well. Mean Absolute Error is a simple average of how far off your predictions are. Mean Squared Error and Root Mean Squared Error both punish bigger mistakes more, which is helpful if large errors are especially bad in your context.

Sometimes, your problem may call for a custom metric that reflects real-world impact better. It all comes down to what matters most for your task.


#### The problem of model overfitting and Regularisation as a fix
Overfitting happens when your model becomes too good at remembering the training data. It picks up not just the real patterns but also the noise. As a result, it performs well on known data but fails on new data.

To fix this, we use regularization. It is a technique that adds a penalty to the loss function for using overly complex models. This encourages the model to be simpler and more general. 

There are a few types of regularization. Ridge penalizes large weights by squaring them. Lasso penalizes weights by their absolute values, which can even set some to zero, effectively removing unnecessary features. Elastic Net combines both. Each method gives you a way to control complexity and help the model focus on what really matters.

### Hands-on Session (Milan De Cauwer and Pubudu)
You can check out the notebook `2.Notebook_Logistic_regression.ipynb`. It is well documented, anyone can follow along easily.

I am not going to discuss this particular notebook in this readme, as I have documented it in my assignment for this workshop that you can find in the main repo itself `assignment_2panad.ipynb`.

