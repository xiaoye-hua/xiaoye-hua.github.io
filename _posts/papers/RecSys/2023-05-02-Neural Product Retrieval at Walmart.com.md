---
layout: post
title: 2019-Neural Product Retrieval at Walmart.com
published: True
date: 2023-05-02
mathjax: True
catalog: true
tags:
  - paper reading
  - RecSys
  - Industry
  - Walmart
---

**Table of Contents**
1. Introduction
{:toc}

		
## Problem Definition

1. Mainly focus on product retrieval in Walmart -> match the query and products
    1. To solve the problem of product retrieval, the key is to assess the relevance between a query and a product. I
2. Two stage model
    1. retrieval
    2. re-ranking 

## Methods

1. All implementation based on tensorflow ranking
2. Pair-wise loss has a better performance than pointwise loss
3. Our neural retrieval model in Section 3 is closely related to CLSM and DSSM.
4. In this section we propose three different models: 
    1. A simple bag-of-token model based directly on tokens in query and product, 
    2. a neural text model which can incorporate semantic similarity between query and product, and
    3. lastly a customized neural text model which is more optimized for
retrieval.
4. Labels: Note that though we are optimizing for
order rate, we did not use order rate as label for training because
order data is sparser compared with click data.
5. Position bias 
    1. a simple click model
	
## TODO & Questions & Further Reading

1. [x] TF ranking
2. [ ] An Introduction to Neural Information Retrieval