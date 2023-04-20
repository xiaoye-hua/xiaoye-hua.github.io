---
layout: post
title: 2020-Improving Deep Learning For Airbnb Search
published: True
date: 2023-04-19
mathjax: True
catalog: true
tags:
  - paper reading
  - RecSys
  - Industry
  - Airbnb
---

**Table of Contents**
1. Introduction
{:toc}

		
## Problem Definition

1. capture the majoy improvement after launching the DNN model.
2. Evaluation method
    1. NDCG 
    2. increasement NDCG (especially for cold start and position bias)
3. Several ideas
    1. But the highlight of our journey is the realization that
to push the boundaries of our DNNs, the inspiration was not going
to come from some external source. For that we had to follow the
lead of our users.
    2. Using NDCG to quantify the position of the booked listings in
search results has been the most reliable gauge of model performance for us.
    3. the price features are easy to learn,  while locaton,  quality are harder to learner. So the initial versions of model will be biased toward price features

## Methods

2. Focusing on three parts: 
    1. architecture -> two-tower architecture with pairwise loss
        1. impact 0.6% in booking, -2.3% in average price, 0.75% in revenue; -33% in 99pertentile latency
    2. Cold start
        1. predict engagement features VS baseline (statistics)
        2. impact: In online A/B experiment, we observed an improvement of +14% in bookings of newly created listings
    2. position bias
        1. Methods 
            1. position as a feature; set it to 0 while doing inference 
            2. use dropout (dropout rate 0.15) for position feature while training,  balancing the relevance prediction and position bias prediction while decding the dropout rate
        3. impact:
            1. 0.7% bookings; 1.8% revenue
	
## TODO & Questions & Further Reading

[ ] more papers from airbnb