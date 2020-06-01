---
layout: post
title: Deep Learning Course Note (Part 6)
subtitle:  Word Embedding
date: 2020-05-30
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

One-hot encoding is easy to implement, however, it can't indicate the similaritiy and analogy relationships between different words. To solve this problem, word2vec is introduced which consists of two model: skip-gram and continuous bag of words. Skip-gram model assumes that the central target word can be generated from the context words. While the CBOW model assumes that the context word can be generated from the central target word. The cross-entropy functions is adopted in the approch of word2vec. However, it can induce some problems such as the overhead of computation. The approch of GloVec utilizes squared loss and word vector to fit the global statistics derived from the whole dataset. FastText proposed subword encoding, which utilizes the priciple of morphology. Based on the skip-gram model in word2vec, fastText takes the central target vector as the sum of subword vetor of words.



# How to Get Word Embedding

## Word2Vec

### Skip-Gram

### CBOW

### Approximate Training
For larger word dictionary, the overhead computing for gradient can be high, two approximate methods are introduced:
1. Negative sampling
2. Hierarchical softmax

## GloVe

## FastText


# Reference
1. [Dive Into Deep Learning Chapter 14](https://d2l.ai/)

