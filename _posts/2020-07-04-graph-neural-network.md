---
layout: post
title: Graph Neural Network
<!-- subtitle:  Reinforcement Learning Basic - Concepts and Taxonomy -->
date: 2020-07-04
published: True
mathjax: True
catalog: true
tags:
  - machine learning
  - GNN
---
# TOC
1. Introduction
{:toc}

# Introduction 
The core assumption of existing machine learning algorithms is that instances are independent of each other. However, this assumption does not hold because each instance is related with each other by links of various types such as citations, friendships and interactions.

# Taxonomy of GNN

<img src='/img/GNN_taxonomy.png' width="900">

Recurrent GNN is the pioneer works of GNN. It assums that nodes in a graph constantly exchanges messages with its neighbors until a equilibruim reaches (Infomation Difussion Mechanism). 

The general ideas behind ConvGNNs is to generate a node's representation from it's own features and its neighbors' features. It falls in two categotries: spectral-based and spatial-based. The first approch defines graph convolution by introducing filters from graph signal processing. The latter method inherit ideas from RecGNNs to define graph convolutions by information propagation.

Graph autoencoders are unsupersized learning which encode graph infomation into latent vector space and reconstruct the graph from the encoded infomation. 

The key idea of STGNNs is to consider spatial dependency and temporal dependency at the same time. STGNNs follow two directions: RNN-based and CNN-based.

# Open Challenges
There are open challenges in the field of GNN:
1. Model depth of the network
2. Scalability trade-off: The scalability of GNN is gained at prices of corrupting graph completeness.
3. Heterogeneity: The mayority of current GNN assume homogeneous graphs.
4. Danymicity: The graphs are in nature dynamic that nodes or edges and appear or disappear, and that node/edge input can change over time.


# Reference
1. [A Comprehensive Survey on Graph Neural Networks](https://arxiv.org/abs/1901.00596)
2. [Composing Graphical Models With Neural Networks with David Duvenaud](https://twimlai.com/twiml-talk-96-composing-graphical-models-neural-networks-david-duvenaud/)
2. [人工智能的下一个拐点：图神经网络迎来快速爆发期](https://www.infoq.cn/article/LjmbcEgqZV6dzXlFRsjf)
3. [深度学习之上，图神经网络（GNN）崛起](https://tech.antfin.com/community/articles/468)