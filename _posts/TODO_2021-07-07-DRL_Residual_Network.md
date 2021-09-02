---
layout: post
title: Residual Network
date: 2021-07-07
published: False
mathjax: True
catalog: true
tags:
  - deep learning
  - machine learning
---
# TOC
1. Introduction
{:toc}

# Introduction
1. Background: Intuitively, layer of DL are used to extract different level of features, and features will be enrich by the number of stacked layers. However, deeper NN has higher train error, namely model degradation.
2. How: ResNet solved the problem of model degradation by adding a shortcut connection besides the main connection. 
    1. Instead of learning the underline map function, the ResNet model tries to learn the residual function between the underline maping function and the input.
    2. In addition, ResNet partly solved gradient vanishing problem.

# Algorithm Details
## Logic

## Structure Details

# Application & Variants


# Questions

1. bypass at least 2 layers ? 


1. VGG16和ResNet152哪个参数量更多？

1. VGG16: 138M
2. ResNet 152: 60M

[Paramters Number Reference](https://keras.io/zh/applications/#_3) 

# Reference
1. [Deep Residual Learing for Image Recognition](https://arxiv.org/abs/1512.03385)
2. [Dive Into Deep Learning](https://d2l.ai/)
3. 

