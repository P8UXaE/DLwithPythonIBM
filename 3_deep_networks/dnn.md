# Multiple hidden layers

A single hidden layer with lots of neurons has the risk of overfitting, but adding more hidden layer decreases the risk of overfitting while increasing the performance. 

A NN with more than one hidden layer is called Deep Neural Network. Each layer can have a different amount of neurons.

# Dropout

Improves the performance. Prevents overfitting. Data is noisy. 

- Too many layers or too many neurons, we risk overfitting.
- If model is overly simplified we risk underfitting.

Instead of trying different combinations of number of neurons and layers (wich takes too much time), we will start with a complex model and apply a form of regularization called dropout. 

Dropout consists in two phases:
- Training phase: we implement the dropout method.
- Evaluation phase, where we turn off the dropout method to test the performance of our model.

## Training phase

Implemented by multiplying the activation function with the Bernoulli random variable r. Bernulli: discrete probability distribution where random variable r takes on the value 0 with probability p, and takes on the value 1 with the probability 1-p. ```r ~ Ber(1 - p)``` p = 0.5 is like flipping a fair coin, r = 0 with probability p or probability of heads, r = 1 with the same probability as tails.

So, If r = 0 in a given neuron, we are shutting off the first neuron in the layer or the first element in the vector.

We apply dropout to the hidden layers during the forward step while training. Probability p tells us how likely we are to shut off a neuron. Probabilities are totally independent; a shut off neuron does not affect the probability of other neurons being shut off (same or other layer).

On each iteration there are different sets of neurons being shut off. 

The larger p, the more neurons we remove, thus preventing overfitting. If p = 0.8 we expect the majority of neurons to not be actibe. If p = 1 then all the neurons will be multiplied by 0. 

Generally, the more neurons the higher the value of p should be used. For the layers with less neurons we use values for p between 0.1 and 0.05, for the layers with more neurons we use a value for p of 0.5.

## Evaluation phase

Here we do not multiply the activation function with the Bernoulli random variable r. We run the NN with all the neurons being active. 

## value of p

p is a hyperparameter. We can obtain the optimal value through cross validation. p very small we risk overfitting. If p is very large we risk underfitting.

If you don't use dropout, the model may decrease the loss value of training but increassing the loss value of validation, while using dropout, the training and validation loss reach a plateau.

# Initializate weights

If you choose the right method, it gets good accuracy with less epochs.

## Default method

It inverses the square root of Lin

## Xavier method

Popular for tanh activation

```torch.nn.init.xavier_uniform(linear.weight) ```

## He method

For relu activation

```torch.nn.init.kaiming_uniform(linear.weight, nonlinearity='relu') ```

# Gradient Descent

...

# Batch Normalization

Batch normalization before we pass the activation function. 

For a given layer we have the outputs of each neuron. We calculate the mean and standard deviation or variance for a particular mini-batch. Normalize the outputs, scale and shift them. These are actually parameters which we're going to learn via training. These outputs will pass through the activation function.

Create BatchNorm object.

Train Loss converges a lot faster.

Why it works? 