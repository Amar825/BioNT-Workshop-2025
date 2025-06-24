## **Day 4 Reflection – [5 June 2025]**

### Theory session- Deep Learning (Elias Myklebust, Simula Research Laboratory)
### **1. Key Ideas Discussed**
#### Deep Learning – A branch of machine learning
Deep learning is basically just machine learning, but with layers. Instead of you designing how to extract features or patterns from data, you give that job to a neural network. It learns those patterns by itself, layer by layer, through training.
#### Shallow Neural Networks
Moving from linear regression to shallow
neural networks

Shallow neural networks are machine
learning models that:
1. Compute linear transformations of the
inputs
2. Pass the results of these
transformations through an activation
function
3. Forms outputs by taking a linear
combination of these ‘activations’
Activation functions – Introducing non-linearity

The activation functions are non-linear
functions that allow the model to capture
non-linear relationships in the output data.
There are many options, but the most
common choice is the rectified linear unit
(ReLU):

Other common choices include sigmoid,
tanh, and variations on ReLU.
Increasing model complexity – adding more
hidden units We can add more hidden units by adding
more linear transformations of the input:

We form the output by creating a linear
combination of these:
Reflection: What happens when we have more
than one input or output?

Extending shallow neural networks to take
multiple inputs/outputs is quite
straightforward.
For multiple inputs, the hidden units would
then be activations applied to linear
combinations of these inputs, e.g.:

The output would still be formed as:
For network with two outputs, we could, e.g.,
have hidden units:

These could then be used to create two
different linear combinations, forming the
two outputs:
The effect of the ReLU activations – Forming
piecewise linear functions

We can add more hidden units by adding
more linear transformations of the input:

We form the output by creating a linear
combination of these:
We can add more hidden units by adding
more linear transformations of the input:

We form the output by creating a linear
combination of these:
Digression: Activations for multiple inputs
Extending shallow neural networks to take
multiple inputs/outputs is quite
straightforward.
For multiple inputs, the hidden units would
then be activations applied to linear
combinations of these inputs, e.g.:

The output would still be formed as:

#### The Universal Approximation Theorem

We can extend shallow neural networks to
have an arbitrary number of hidden units. In
a network with D hidden units, we can
describe the hidden units as:

And the network output as:

The universal approximation theorem states
that for any continuous function, there exists
a shallow network that can approximate it.

### Deep networks
From shallow to deep – Adding another
network

A simple way to extend our shallow network
would be to pass the output through a new
network.

We would then pass the output of the first
network to new hidden units:

And create a final, new output:
From shallow to deep – Changing perspective

If we insert the original expression for the output of the first network into the expression we
had for the new hidden units, we get:
We can now define a deep network with two
layers, where the first hidden layer is:

The second hidden layer is:

And the final output is:
Reflection: How does the second layer modify
the output of the first layer?
Digression: Matrix notation and GPUs

Using matrix notation, we can the hidden layers in our two-layer network as:

And the output as:

37

Digression: Matrix notation and GPUs

We write this even more compactly as:

GPUs are highly optimized for doing matrix
operations in parallel. This is why they are so
effective at speeding up the computations
needed to do deep learning.

38

In general, deep networks can handle any number
of inputs, outputs, layers and hidden units

In general, we would express a network as

39

Figure borrowed from Prince, S. J. (2023). Understanding deep learning. MIT press.

Deep networks – Parameter counts and
number of linear regions

A network with one input, K layers and D (>2)
hidden units in every layer would have a
parameter count of

Such a network could create a function with

linear regions.

40

Figure borrowed from Prince, S. J. (2023). Understanding deep learning. MIT press.

Reflection: Why choose deep networks when the
universal approximation theorem holds for shallow
networks?

• There are functions for which shallow networks need exponentially
more hidden units than deep networks to approximate them

• More advanced architectures that make more e9icient use of the
available parameters are easier to specify with multiple layers

• It is often easier to train (moderately) deep networks than shallow ones

• Deep networks typically generalize better to new data than shallow
networks
#### Training nurwal networks
Training neural networks – Tuning parameters
until the model is ‘good’

On a high level, training neural networks
consists of two steps:
1. Defining a what a good model means for
our problem through a loss function
2. Using an optimization algorithm to find
parameter values that minimize the loss
function

43

What is a loss function?

A loss function is a function of the model
parameters that describes the mismatch
between the model predictions and their
associated ground truth values.
It is typically formulated such that a smaller
loss reflects better model performance.
Thus, once we have defined our loss
function, we train our model by seeking
parameter values that minimize the loss.

44

The maximum likelihood approach for creating
loss functions

A common framework for creating loss
functions is the maximum likelihood
approach.
Instead of thinking of the model as directly
predicting an output y given an input x, we
shift perspective, and treat the model as
predicting a conditional distribution over
possible outputs, given the input:
Given this perspective, we want the loss
function to encourage a high probability for
the training outputs, i.e., we maximize
across all samples.

45

Figure borrowed from Prince, S. J. (2023). Understanding deep learning. MIT press.

The maximum likelihood approach –
Predicting distribution parameters

Under this framework, we set the network to
predict the parameters of the conditional
distribution, i.e., we set

For the conditional distribution . We
then find model parameters

46

The maximum likelihood approach – Negative
log-likelihood

Since the probabilities in the maximum
likelihood criterion often become small, and
thus their product can become hard to
represent with finite precision arithmetic in
computers, we take the logarithm of the
previous expression.
Additionally, since model fitting is framed as
a minimization problem by convention, we
multiply by negative one. Thus, we get

47

Figure borrowed from Prince, S. J. (2023). Understanding deep learning. MIT press.

The maximum likelihood approach – A recipe
for creating loss functions

1. Define a suitable probability distribution
over the output space;
2. Set the model to predict the parameters
of this distribution;
3. Find the model parameters that best fit

the data by minimizing the negative log-
likelihood loss function

For predicting on a new sample x, we either
return the full distribution ,
or its maximum.

48

Example: Binary classification – The output
space

In binary classification, we try to predict
whether an input belongs to one of two
classes. Our output space can therefore be
defined as

To construct a loss function for this problem,
we begin by defining a suitable probability
distribution over the output space.
The most natural choice for binary
classification is the Bernoulli distribution:

49

Figure borrowed from Prince, S. J. (2023). Understanding deep learning. MIT press.

Example: Binary classification – The sigmoid
function

To ensure that our network output can
describe such a probability, we need to force
the it to be between 0 and 1.

To this end, we employ the sigmoid function:

50

Figure borrowed from Prince, S. J. (2023). Understanding deep learning. MIT press.

Example: Binary classification – The loss
function

We can rewrite the Bernoulli probability
distribution as

With this rewrite, we can define the
likelihood as

Finally, we take the negative logarithm to
obtain the negative log-likelihood:
Fitting models – Gradient descent

We have defined the loss function, and now
need to find the parameter values that
minimize it.

Gradient descent is an optimization
algorithm that uses gradient of the loss
function to minimize it.

53

Fitting models – Gradient descent

We have defined the loss function, and now
need to find the parameter values that
minimize it.

Gradient descent is an optimization
algorithm that uses gradient of the loss
function to minimize it.

54

Fitting models – Gradient descent

We have defined the loss function, and now
need to find the parameter values that
minimize it.

Gradient descent is an optimization
algorithm that uses gradient of the loss
function to minimize it.

55

Fitting models – Gradient descent

We have defined the loss function, and now
need to find the parameter values that
minimize it.

Gradient descent is an optimization
algorithm that uses gradient of the loss
function to minimize it.

56

Fitting models – Gradient descent

We have defined the loss function, and now
need to find the parameter values that
minimize it.

Gradient descent is an optimization
algorithm that uses gradient of the loss
function to minimize it.

57

Gradient descent – The algorithm

The gradient descent algorithm has two
simple steps:
1. Compute the gradient of the loss w.r.t.
its parameters:

2. Update the parameter values:

Here, alpha determines the rate of change,
and is typically called the learning rate.

Stochastic gradient descent – Introducing
noise to the optimization algorithm SGD – Training on random mini-batches at
each step

In general, our loss functions can be thought
of as a sum of loss terms for each training
sample:

In regular gradient descent, we include all of
these terms in the computation of the
gradient.
In SGD, we introduce randomness by only
computing the gradient for a random subset
of the samples at each step:
Batches, epochs, monitoring and
checkpointing

The subset of training samples that we use
for each update is called a batch. The
number of elements in the batches can vary
from one to the entire training set, in which
case we are back at regular gradient
descent.

When we have small batch sizes, we need
several iterations to cover the entire training
set. A full pass through the training set is
called an epoch.
In practice, we often make checkpoints, and
monitor progress at each step.

66

Digression: The backpropagation algorithm

The backpropagation algorithm is an
efficient way of computing derivatives in a
neural network, that applies the chain rule.
It involves doing a forward pass, where we
compute (and store) all the intermediate
values needed to calculate the loss.

Once we have calculated the loss, we can
compute derivatives of all the intermediate
variables, applying the chain rule.

Specialized architectures – Modifications to
deal with complex inputs, etc.

We have now looked at the basic
components of deep learning models, what
functions they represent and how we can
train them.

Specialized architectures have been
developed to deal with task specific
problems such as large inputs, inputs of
varying length and spatial or textual context.
Examples of such architectures include
convolutional neural networks for image
analysis and transformers for text
processing.
