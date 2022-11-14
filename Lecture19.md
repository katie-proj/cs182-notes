# Lecture 18

## Logistic Regression
Sum of weighted inputs ``x_i w_i`` gets fed into sigmoid function.

## Neural Networks
Hidden layers are the layers in between input and output. Each node is called a **unit**, which 
calculates the weighted sum of its predecessors and applies an activation function to it.

### Activation Fucntions
- if the activation function is identity, then the whole function is just linear
- the choice of activation functions is very important, source of expressivity of neural networks
- examples: sigmoid, ReLU, softplus

## Training Neural Networks
A chocie of network architecture (units, activation functions, and edges) defines a hypothesis space 
whose parameters are the weights on edges. 
- with just two layers and nonlinear activation functions, neural networks can approximate any continuous function arbitrarily well
- training is usually done by gradient descent

Computing the gradient can be expensive. Once the gradient is computed, take steps in the direction of the gradient. 

## Input Encoding 
Categorial features are typically encoded using 1-hot encoding (1 in index of category it is, 0 elsewhere). 

## Output Encoding
**Binary Classification**: sigomid output unit is used, and output is interpreted as the probability 
of the positive class  
**Multiclass Classification**: we want d output nodes representing probabilities summing up to 1, 
this is typically done via softmax layer  

## Convolutional Neural Networks
CNNs make use of two ideas:
1. to respect adjacency, each hidden unit receives input from a local region of the image
2. anything detectable in one local region would look the same in another local region  

A pattern of weights is called a **kernel**, and an application of the kernel is a **convolution**. It is often desirable to pad the image with 0s at the 
edges to not lose information about them (due to kernel not being 1x1).

## Receptive Field
The receptive field of a unit is the portion of th einput that can affect the unit. 

## Pooling
A pooling layer summarizes adjacent units from a preceding layer. Very similar to convolution, but uses a fixed operation rather than some kind of learning 
(weights are not configured). 
- average pooling: computes the average value of inputs
- max pooling: computes the max value of inputs

Pooling will generate a low-resolution version of the original image. 

## Sequential Memory
We can drop the assumption that the neural network is acyclic. 

### Recurrent Netowrks
In a recurrent neural network, units take thier own output as input, which simulates memory. RNNs are typically used to analyze sequential data, just like 
HMMs. We make a Markov assumption.
