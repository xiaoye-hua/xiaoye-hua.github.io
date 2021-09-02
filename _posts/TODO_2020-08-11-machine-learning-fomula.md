---
layout: post
title: Deep Learning Interview Questions 
<!-- subtitle: Deep Learning Explain Series (Part 1) -->
date: 2020-08-02
published: False
mathjax: True
catalog: true
tags:
  - machine learning
---
# TOC
1. Introduction
{:toc}

# Introduction
 "when you go through this process, you'll find there are many thing you think you understand but you didn't. You will make connections that you didn't see before and simplied the the information in your head as you try to condense it down and regurgitate it... This step is crucial to retain information and developing more than a surface-understanding of a subject" 

# Question & Answer
Three question to ask:
- The purpose of this technique
- Steps of this technique
- How these steps contribute to the goal?

### What's gradient descent?
Ref[1][2]
- Gradient descent is used to minimize the cost function by move in the direction of the steepest descent. And the direction of steepest descent is define by the negative of gradient. We used gradient descent to update the parameters of model.

### What do you understand by backpropagation?
Ref[1][2]
- The goal of backpropagation is straightforward: utilizing gradient descent technique, adjust the weights of NN in propotion to the how much contributes it makes to the total error. The intuition is that: if we iterratively reduce each weight's error, finally we can get the weights that make the best predictions

### What is "data normalization"?
Ref[2]
- The goal of data normalization is to accelerate the convergence of NN.
- The input datas take values with widely varing magnitudes. Usually we'll normalize it to have a zero mean and unit variance.
- In this case, all the input value fits into a similar range, which can help to achieve better convergence.

### What's the role of activation functions?
- The activation function will decide whether the neuro will be activated of not. It accepts weight sum as input. Usually, it will add non-linearity
- Typical activation functions are: 
	- sigmoid function: $Sigmoid(z)=\frac{1}{1+e^{-z}}$
	- tanh function: $Tanh(z)=\frac{e^x-e^{-x}}{e^x+e^{-x}}=\frac{1-e^{-2x}}{1+e^{-2x}}$
	- ReLU(Rectified Linear Unit) function: $ReLU(z)=max(z, 0)$
	- softmax function: $softmax(z_i)=\frac{e^{z_i}}{\sum_j e^{z_j}}$

### What's the difference betweeen feedforwd neural network and recurrent neural network?
- In feedword neural network, signal can only go one direction, there is no loop in the network. It can't remember the previous input
- In recurrent NN, the signal travels in both directions, so there are loops. It both considers the current input and the previous input to create the output signal.

### What's the paramters and hyper paramters of deep learning ?
- Paramters of the model refers the goals of training, namely the weight and bias of the model
- Hyper paramters refers the value that are set before training. It determines how the model are trained and the structures of the model. Such as learning rate, batch size, number of hidden layers, hidden neurons.


### What will happend if the learning rate is too low or too high?
- Too low: progress very slowly, the training will be time-consuming
- Too high: sometimes it will fail to converge

### What is the difference between batch gradient descent and stochastic gradient descent:
- Batch gradient descent compute the gradient use the entir dataset. It's not possible to use it when the dataset is too large; 
- Stochastic gradient descent uses only one sample. It's not computational efficient because the CPU and GPU can not utilize the power of vetorization.

### How to combat overfitting in deep learning?
1. We can use regularization technique to combat overfitting.
2. How to
	- Dropout
	- Early stopping 
	- Add L1 or L2 regularization term to our objective function
	- Utilizing ensembling technique

### How are weight initialized in NN?
Ref[2][3]
- Set the weight all to zero.  
- Initialized them randomly 
- Initialize from the function such Xavier, He

### What are the different layers in CNN? Explain the role of each kind of layer?
1. Full connected layer:
2. Convolutional layer: convolutional opreation, extract hidden features
3. Batch nomalization layer: 
4. Pooling layer: down-sample operation, reduce dimension of feature.

### Dropout
- Dropout is a technique to reduce overfitting. It introduces noise while computing the hidden layer in the forward propagation.
- Throughout the training, every iteration, this technique will zero out fractions of nodes before computing the subsequent layer.

# Ref
1. [ML Glossary](https://ml-cheatsheet.readthedocs.io/en/latest/gradient_descent.html)
2. Dive into Deep Learning
3. [深度学习的参数初始化](https://blog.csdn.net/mzpmzk/article/details/79839047)


