---
layout: post
title: Neural Network
categories: machinelearning
sitemap: false
hide_last_modified: true
published: true
---
## [ML] Neural Network

### Perceptron model

- single biological neuron < perceptron < multi-layer perceptron model < deep learning neural network
- perceptron model replicating the core concepts behind a biological neuron
- term(perceptron = neuron)
- different types of layers and different network configuration - recurrent, convolution
- hidden layers are difficult to interpret, due to high interconnectivity and distance away from known input or output values
- If it contains two or more hidden layer, it’s deep neural networks
- neural network framework can be used to approximate any function
- in single perceptron summation function: took our inputs X, multiplied them by their own weights W, added bias, and summed it all up
- tensor: n-dimension matrix

### Activate functions

- activation functions: in a classification tasks, it would be useful to have all outputs fall between 0 and 1, and these values can then present probability assignments for each class.
- basic Step function: 0 or 1
- Logistic/Sigmoid(soft step): 0 ~ 1
- Hyperbolic Tangent(TanH): -1 ~ 1 (lower bound is -1)
- Rectified Linear Unit(ReLu): max(0, z), good performance especially when dealing with the issue of vanishing gradient
- Multi-class activation functions → one-hot encoding
    - non-exclusive classes (i.e. multi tags for photo)
        - sigmoid
    - mutually exclusive classes (i.e. grayscale or full colour photo)
        - softmax function: calculates the probabilities distribution of each target class over all possible target classes
        - the range will be 0 to 1 and the sum of the probabilities will be equal to one
        - the target class chosen will have the highest probability

### Cost functions

- the output `\hat{y}` is the model’s estimation of what is predicts the label to be
- how do we evaluate it? and after the evaluation, how can we update the networks, weights and biases? (during training/fitting )
- Cost functions
    - compare our neural networks output to the true value
    - measures how off you are from the true value based off your prediction
    - = loss function, error function
    - must be an average so it can output a single value
    - we can track of our cost/loss during training to monitor network performance, hopefully during each epoch of training, cost/loss goes down until converge to some minimum cost value.
- Gradient descent
    - calculate the slope at one point and then move in the downward direction of the slope
    - keep repeating this until converge to zero which is minimum error
    - can choose step size for next slope (→ learning rate, how fast they’re going to try to find that minimum weights and biases)
    - smaller step sizes takes longer to find the minimum
    - larger step sizes are faster, but we risk overshooting the minimum
    - learning rate can be constant or adapt step size as we go along → adaptive gradient descent
    - Adam Optimiser: efficient way of searching for minimums, adaptive gradient descent algorithms
    - n-dimensional vectors(tensors) the notation changes from ‘derivative’ to ‘gradient’
- Backpropagation
    - once we get our cost/loss value, how do we actually go back and adjust our weights and biases?
    - calculate error in last layer and going backwards through the network to calculate all those errors and then adjusting the weights and biases accordingly to minimise that cost function

### TensorFlow vs Keras

- TensorFlow: open-source deep learning library developed by Google
- Keras: high-level python library that can use a variety of deep learning libraries underneath
- TensorFlow 2.x adopts Kereas as a official API

### Keras

- epoch: one pass over the entire dataset
- mean_absolute_error: how far off we are. good or bad? depend on your original data, always have to take into account the mean values as well as the actual distribution of your label
- batch_size: for larger data set, we feed in our data in batches, typically powers of two, the smaller the batch size, the longer training is going to take, but the less likely overfitting because you’re not passing in your entire training set at once
- dense: base the number of neurons (or units) in our layers from the size of actual the feature data (X_train.shape → i.e. model.add(Dense([number of column], activation=’relu’))
- callbacks (early stopping): based on validation loss, stop the training before it gets out of hand and fall into overfitting
- dropout layer
    - can be added to layers to turn off neurons during training to prevent overfitting
    - each dropout layer will drop user-defined percentage of neuron units in the previous layer every batch

### Code
<iframe src="https://nbviewer.org/gist/soyeonkimgithub/902c88eddb070f1a4c92958666a65129" width="1000" height="1500" scrolling="yes" frameborder="1"></iframe>
