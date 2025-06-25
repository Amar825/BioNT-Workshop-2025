## **Day 3 Reflection – [4 June 2025]**
## Table of Contents

- [Theory Session – Model Optimisation and Validation (Katarzyna Michałowska, SINTEF Digital)](#theory-session--model-optimisation-and-validation-katarzyna-michałowska-sintef-digital)
  - [Key Ideas Discussed](#key-ideas-discussed)
    - [Overfitting](#overfitting)
    - [Bias Variance Trade-off](#bias-variance-trade-off)
    - [Data Splitting](#data-splitting)
    - [Data Leakage](#data-leakage)
    - [Hyperparameter Tuning](#hyperparameter-tuning)
    - [Evaluation](#evaluation)
    - [Model Robustness](#model-robustness)


### Theory session- Model Optimisation and Validation (Katarzyna Michałowska, SINTEF digital)
### **1. Key Ideas Discussed**
#### Overfitting
This happens when our model gets too good at remembering stuff from the training set and starts picking up patterns that aren’t actually useful, like noise. It looks like it's doing great, but once you give it real-world data, it crashes. That’s overfitting. It’s why we don’t just care about training accuracy.
#### Bias varaiance trade off
Models can go wrong in two main ways. Bias means your model is too simple and completely misses the point. Variance means our model is too sensitive and changes its mind based on tiny differences in data. The sweet spot is somewhere in the middle. Getting there depends on how complex your model is and how you train it.
#### Data Splitting
We always split the dataset into training, validation, and test. Train on the first, tune using the second, and report final results on the third. Touching your test set early basically ruins it. Cross-validation is just a smarter way to rotate through the splits, especially when you have limited data.
For time series data, things get trickier. We can’t just shuffle and split randomly, because the future shouldn't influence the past. Always make sure our training set comes before your validation and test sets in time. Think of it like trying to predict tomorrow using only what you knew yesterday, not the other way around.

#### Data Leakage
Data leakage is when our model accidentally sees the answer key during training. Like scaling the entire dataset before splitting or using features that wouldn’t exist at prediction time. The result is artificially high performance, and the model fails later in production. Fix it by being strict: split first, transform later. Always check if the model could actually access that info in real life.

#### Hyperparamter tuning
These are the settings you choose before training. Like max depth in a decision tree, or learning rate in a neural network. Some hyperparameters control how complex the model can get, which ties directly into the bias-variance problem. You usually don’t know the best values in advance. That’s why we use grid search or random search to try out combinations. 

Grid search works well when we have  few hyperparameters and want to test every possible combination. It makes sense when we already have a rough idea of the ranges that matter. But if we are working with many parameters or a big search space, random search can be more efficient. It skips the exhaustive sweeps and samples combinations that are more likely to be useful. So, use grid search for small, focused problems and use random search when things get large or messy and we just want to cover ground quickly.


#### Evaluation
Always compare the model to something dumb first. A baseline could be a model that just predicts the mean or the most frequent class. If your model can’t beat that, it’s not worth using.
For classification, accuracy might look fine until you realize your model’s just guessing the majority class. Use precision and recall together. One tells you how many of your predictions were right, the other tells you how many true cases you found. For regression, MAE is easy to interpret. MSE punishes big mistakes more. .

#### Model robustness
Robustness means our model doesn’t fall apart when something slightly changes. New data might be noisier, or slightly different than what it saw before. If our model only works in perfect conditions, that’s not useful.
