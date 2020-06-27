---
layout: post
title: Review about customer-life-time-value(CLTV) Prediction
<!-- subtitle:  Reinforcement Learning Basic - Concepts and Taxonomy -->
date: 2020-06-20
published: True
mathjax: True
catalog: true
tags:
  - machine learning application
  - review
---
# TOC
1. 背景
{:toc}

# 背景

用户的价值与公司的商业价值直接相关。如果能够预测用户在未来一段时间内的价值，公司可以把资源集中在价值高的用户群中，得到更高的投入产出比。同时根据预测所得的用户分层可以进行一下运营活动

1. 用户获取
2. 用户服务
3. 产品内购买
4. 定价和促销

# 建模方法

## Customer Lifetime Value Prediction Using Embeddings

预测步骤:

由于LTV数量级分布差异比较大, 故做了两级预测:

RF模型预测用户的LTV大小在总体分数的分位(范围0-1)

RF模型将预测的分位映射到LTV的具体述职

## An Engagement-Based Customer Lifetime Value System for E-commerce

预测步骤:

由购买频率, 将用户分成6层, 分别建模分析

对不同分层内, 预测用户在未来一个时间段是否会有购买行为

对于预测会购买的用户, 预测其LTV 


