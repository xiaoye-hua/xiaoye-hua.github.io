---
layout: post
title: 2013-Learning Deep Structured Semantic Models for Web Search using Clickthrough Data
published: True
date: 2023-03-26
mathjax: True
catalog: true
tags:
  - paper reading
  - RecSys
  - candidate generation
---

**Table of Contents**
1. Introduction
{:toc}

DSSM was initial invented for NLP word-matching task, recent years, it is widely used in candidate generation stage of recommendation system.



## Problem Definition

1. Main objective:
    1. web document ranking task
2. Main metrics (only offline evaluation available)
    1. NDCG@1, 3, 5

## Previous Methods & new Methods & mainly contribution


1. Main contributions
    1. [x] learning from clickthrough data
    2. [x] DNN supervised learning
    2. [ ] word hashing: n-gram based word hashing
    

## Application in RecSys

1. Pros: 
    1. fast: item-embedding calculated offline; user-embedding calculated in real-time
2. Cons:
    1. no interaction between item and user features

## Ref 

1. [为什么现在推荐系统喜欢用双塔模型？双塔模型相较于单塔有什么优缺点？ - 数据拾光者的回答 - 知乎](https://www.zhihu.com/question/390201026/answer/1633392847)
2. [推荐系统(十八) 大厂实践经验学习：双塔模型 - 缄默笔记的文章 - 知乎](https://zhuanlan.zhihu.com/p/495737522)
3. [读透Learning Deep Structured Semantic Models for Web Search using Click through Data](https://zhuanlan.zhihu.com/p/363658235)


## TODO & Questions & Further Reading

1. [x] Latent Semantic Model: intend to map a query to its relevant documents at the semantic level where keyword-based matching often fails
2. [x] get cosine similarity, then apply softmax -> yes
3. [ ] word hashing: letter n-gram
4. to read
    1. [ ] Sampling-Bias-Corrected Neural Modeling for Large Corpus Item Recommendations: from google 2019, tried to removed the influence of popular item to negative sampling
        1. [ ] in-batch softmax ??就是利用batch内样本互相做彼此的负样本，来构建softmax损失
    2. [ ] Embedding-based Retrieval in Facebook Search: from facebook 2022
    3. [ ] [deepmatch DSSM example](https://t.zsxq.com/0cuPUvjUl)


