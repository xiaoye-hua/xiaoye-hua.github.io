---
layout: post
title: 2010-Factorization Machines
published: False
date: 2023-04-04
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

A classic paper from Youtube in 2016, which including both DNN model structures and feature engineering tricks.
		
		
## Problem Definition

1. Problem definition -> increase watch time 

## Previous Methods & new Methods

1. Previous:
    1. two stages model 
        1. Candidate generation: matrix factorization trained with rank loss
        2. Ranking model: linear or tree based watch time prediction (regression)
2. New: Classic two-stage structure
	1. candidate generation
		1. Method: U2I (user-item similarity)
		    1. video vectors are trained with word2vec
		2. Metrics: MAP (Mean Average Precision)
	2. ranking: 
		1. Method: DNN (similar structure as CG) + weighted LR ??
		2. Objective: function of expected watch time per impression (watch time better capture engagement)
		3. [ ] Metrics watch time-weighted pairwise loss
		    1. the cross entropy loss was adjusted

## Impacts

1. No number about the increasement


## TODO & Questions & Further Reading

1. [ ] ranking model -> predict watching time??
2. [ ] time age as input??
    1. model is biased on historical data, while users like new content
    2. age of the training samples is included as feature, At servingtime, this feature is set to zero (or slightly negative) to reflect that the model is making predictions at the very end
of the training window.
3. [ ] matrix factorization trained with rank loss
4. [ ] weighted LR
5. [ ] feature engineering of ranking
    1. [ ] time since last watch -> how to normalize
        1. A continuous feature x with distribution f is transformed to ˜x by scaling the values such that the feature is equally distributed in [0, 1) using the cumulative distribution,
        
        
        
        
## Ref

1. [重读Youtube深度学习推荐系统论文，字字珠玑，惊为神文 - 王喆的文章 - 知乎](https://zhuanlan.zhihu.com/p/52169807)
2. [YouTube深度学习推荐系统的十大工程问题 - 王喆的文章 - 知乎](https://zhuanlan.zhihu.com/p/52504407)
3. [揭开YouTube深度推荐系统模型Serving之谜 - 王喆的文章 - 知乎](https://zhuanlan.zhihu.com/p/61827629)