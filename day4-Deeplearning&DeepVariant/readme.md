## **Day 4 Reflection – [5 June 2025]**

### Theory session- Deep Learning (Elias Myklebust, Simula Research Laboratory)
### **1. Key Ideas Discussed**
#### Deep Learning – A branch of machine learning
Deep learning is basically just machine learning, but with layers. Instead of you designing how to extract features or patterns from data, you give that job to a neural network. It learns those patterns by itself, layer by layer, through training. This is why deep learning shines in areas like image recognition or biological sequences, where the relationships in the data are complex and hard to hand-engineer.
#### Shallow Neural Networks
We start with shallow networks, which just means one hidden layer between the input and the output. Even this simple setup is already more flexible than something like linear regression. The key is in the activation function.  With an activation function, you introduce non-linearity, and suddenly you can model much more interesting relationships.

#### Activating Functions
This part is I think one of the most important building blocks. An activation function is what allows the network to stop being just a stack of linear equations. Rectified Linear Unit (ReLU) is the most common choice. It’s simple: if the input is positive, keep it. If not, set it to zero. That small trick makes learning efficient and keeps gradients stable.

But ReLU isn’t the only choice. Sigmoid and tanh were common in earlier models. Sigmoid squashes values between 0 and 1, which is great for binary classification but not so great for gradient flow. Gradient flow just means how well the learning signal moves backward through the network. When gradients flow properly, each layer knows how much it needs to adjust to improve the final output. But if gradients vanish or explode, some layers get no useful feedback, and training either stalls or becomes unstable. Tanh is similar but centered around zero, which can help in some cases. Then there are more exotic ones like leaky ReLU or GELU, but the main idea is the same, squash the input to allow the network to learn more complex, non-linear patterns.

#### Loss Functions and Max Likelihood
Loss functions are how the model learns. They measure how wrong the prediction is and guide the network to adjust itself accordingly. In binary classification, the most commonly used loss is cross-entropy. But where does it come from?
The idea is to shift perspective. Instead of predicting a label directly, the model predicts a probability for each label. You then ask, how likely is it that the model would have made this prediction if the label were correct? That likelihood becomes the thing you want to maximize.
But since multiplying small probabilities can quickly get messy, we take the log of the likelihood, which turns multiplication into addition. Then we flip the sign because most optimizers are built to minimize, not maximize. This gives us the negative log-likelihood, also known as cross-entropy loss.

#### Training with Gradient descent
Once we have our loss function, we need to minimize it. That is what gradient descent is for. It tells you how much each parameter contributes to the error and in what direction to adjust it.

You take small steps downhill in the loss landscape. The size of those steps is set by the learning rate. If the steps are too big, you might bounce around and miss the minimum. If they are too small, the training takes forever. It is all about finding a good balance.

#### Batches, epochs, and monitoring
Instead of feeding the whole dataset into the model at once, we divide it into batches. A batch is just a small group of data points used to estimate the gradient. This makes training more efficient and adds some noise that can actually help generalization.

One full loop over the dataset is called an epoch. You usually train for multiple epochs, adjusting weights along the way. At the end of each epoch, you check how the model is doing on a validation set. If performance improves, great. If not, maybe you are overfitting or your learning rate is off.

#### Backpropagation
This is the engine that makes deep learning possible. Backpropagation lets you compute the gradient of the loss with respect to every weight in the network, efficiently. It applies the chain rule from calculus to trace how each weight influenced the final prediction.

You run a forward pass to get predictions and loss. Then in the backward pass, you compute gradients by moving backward through the network. Each layer hands off its gradient to the one before it. This lets the optimizer adjust every parameter correctly.

