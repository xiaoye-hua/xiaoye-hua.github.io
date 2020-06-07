---
layout: post
title: Word Embedding
subtitle: Deep Learning Course Note (Part 6)
date: 2019-02-20
published: True
mathjax: True
catalog: true
tags:
  - deep learning
  - machine learning
  - 学习笔记-course note
  - 公开课-MOOC
---
# TOC
1. Introduction
{:toc}


# Introduction
This is the course notes of deep learning specialization. 

# Definition & Usage

Word embedding is a technique to map words to vector of real numbers. There are several apporches:
1. One-hot encoding
2. Word2vec (Word to Vector)
	1. Skip-Gram model 
	2. CBOW (Continuous Bag Of Words) model
3. GloVe (Encoding with Global Vector)
4. Subword encoding such as fastText

One-hot encoding is easy to implement, however, it can't indicate the similaritiy and analogy relationships between different words. 

To solve this problem, word2vec is introduced which consists of two model: skip-gram and continuous bag of words. The cross-entropy functions is adopted in the approch of word2vec. However, it can induce some problems such as the overhead of computation. 

The approch of GloVec utilizes squared loss and word vector to fit the global statistics derived from the whole dataset. FastText proposed subword encoding, which utilizes the priciple of morphology. Based on the skip-gram model in word2vec, fastText takes the central target vector as the sum of subword vetor of words.


# How to Get Word Embedding

## Word2Vec

In the approch of word2vec, by learning a langage model, we extract the weights of the language model as the vector of specific words. There are two type of language model: skip-gram and continuous bag of words. In both model, each word is represented by two d-dimension vector: $v_i\in R^d$ when it is the central target words, $u_i\in R^d$ when it is the context words. In the application of NLP, central target word vector in skip-gram is used, while context word vector is used in CBOW.

### Skip-Gram

Skip-gram model assumes that the central target word can be generated from the context words. The probability of generating the context words given the central word can be obtained by performing a softmax operation on the vector inner product:

$P(w_o\|w_c)=\frac{exp(u_o^Tv_c)}{\sum_{i\in V}exp(u_i^Tv_c)}$

By apply maximium likelihood estimation, we can get the objective function, and optimize it with gradient descent algorithms.

### CBOW
While the CBOW model assumes that the context word can be generated from the central target word. 

### Approximate Training
Due to the structure of cross-entropy objective function, for larger word dictionary the overhead computing for gradient can be high, two approximate methods are introduced:
1. Negative sampling
2. Hierarchical softmax

## GloVe

GloVe adopted square loss and make change to skip-gram model based on the loss. In addition, the central target word vector and context vector are the equivalent in GloVe.


# Application of Embedding

Word2vec has been applied successfully in many field besides NLP. Check references for more application.


# Reference
1. [Dive Into Deep Learning Chapter 14](https://d2l.ai/)
2. [秒懂词向量word2vec的本质(可深入阅读里面的参考文献)](https://zhuanlan.zhihu.com/p/26306795)
3. [时序数据与embedding (embedding 在NLP外领域的应用)](https://zhuanlan.zhihu.com/p/144030067)

