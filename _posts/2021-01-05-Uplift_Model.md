---
layout: post
title: Uplift Model
date: 2021-01-05
published: True
mathjax: True
catalog: true
tags:
  - machine learning
  - causal inference
---
# TOC
1. Introduction
{:toc}


# 总结

关于ROI相关的技术大部分集中在

casual inference : uplift model, propensity score

optimazation problem   

# 2020 - Free Lunch! Retrospective Uplift Modeling for Dynamic Promotions Recommendation within ROI Constraints

TODO
1. 问题定义
2. 线上效果  如何解读
3. AUUC 等评估指标
3. 背包问题 Knapsack Problem
4. 本文中的ATE具体是指啥 -->  averge target effect
5. Retrospective Estimation
6. transformed outcome uplift
7. 业务相关
    1. 文中的return 算的是几天的， 1天太短，随机性太大，7天的话，后面的收入确实是由于这个订单造成的？

# Problem

公司：booking.com

In this work, we focus on maximizing the overall number of customers completing a purchase, while deciding whether or not to offer the promotion in order to comply with the global constraint of ROI ≥ 0.

在ROI>0的情况下，尽可能的扩大受惠人群

# Previous & Current Method

uplift 没有考虑cost factor

## Previous 

uplift model

## Current

1. predict uplift, return & cost
2. Solve it with knapack problem
3. Retrospective Estimation 

# Result & Conclusion & Insight
<img src='/img/uplift_model/result1.png' width="600">


# Limitation & Possible Direction

Our contributions lay the foundation for future research to apply the Retrospective Estimation technique to other uplift modeling and personalization applications. This sets the groundwork for new optimization approaches and provides solid empirical evidence of the benefits of online personalized promotion allocation and dynamic calibratio


# 2019 - Uplift Modeling for Multiple Treatments with Cost Optimization

TODO
1. multi-armed bandit framework.  --> 大体原理知道
2. X-learner    R-learner --> 大体原理懂了
3. 倾向性得分模型 (propensity score)?    --> causal inference book & code
4. 人工数据是如何生成的？

## Problem & Contributions

### Problems:

Uplift model for multiple treatments with multiple costs

Two common cost
1. fixed impression cost for each user
2. triggered cost for user  (promotion cost)

### Contributions

1. extended existing framework of meta-learing to the multi-treatment
2. proposed the net value optimazation to take the value of conversioin and varying costs of different treatments

Related works 部分的review很好，可以作为参考

## Methods
<img src='/img/uplift_model/method.png' width="600">

注： 这里的Y指某个用户是否转化

### Previous

uplift model only

### Current

uplift model + net value optimazation

<img src='/img/uplift_model/current.png' width="600">

注： net value 指单个用户带来的收益

## Result & Conclusion & Insight

Result: The highest net value for NV-RLearner and NV-XLearner

<img src='/img/uplift_model/result2.png' width="600">

Possible direciton:
1. practical challenge such as the quality of training data
2. extended the uplift model to regression problem

# 2019 - Alibaba - A Unified Framework for Marketing Budget Allocation

TODO

logit demand curve

## 背景 & 解决办法

1. semi-black-box model is built to forcast the dynamic market response
2. effcient optimization algorithm to solve the complex allocation task

<img src='/img/uplift_model/framework.png' width="600">


## Evaluation 

<img src='/img/uplift_model/result3.png' width="600">

在开源数据和公司数据上都有验证


