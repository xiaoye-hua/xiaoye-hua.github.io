---
layout: post
title: 2018-Applying Deep Learning To Airbnb Search
published: True
date: 2023-04-16
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

This paper is an interesting industry paper from Airbnb. The most interesting part is that it's closer to real-world application and it should the things they've tried and failed in Airbnb. I'll need to re-read this paper to understand more.
		
		
## Problem Definition

1. Problem definition -> increase bookings
2. Principle offline metrics: NDCG


## Methods

1. Gain of DNN: Earlier the focus was largely on feature engineering, but aer the move to deep learning, trying to do beer math on the features manually has lost its luster. is has freed us up to investigate problems at a higher level, like how can we improve our optimization objective, and are we accurately representing all our users?
2. Model evolution
    1. Manually crafted score function 
    2. GBDT
    3. Simple NN
    4. Lambdarank NN
    5. GBDT + FM
    6. Deep NN
2. Feature engineeing
    1. 2 transformation - feature normalize to with the bulk of the distribution x in the {-1, 1} interval and the median mapped to 0.
    2. [ ] In addition to mapping features to a restricted numerical range, we ensured most of them had a smooth distribution.
    
## TODO & Questions & Further Reading

1. [ ] How can we test if the model is generalizing well beyond logged
examples? e real test is of course online performance of the
model, but we found the following technique useful as a sanity
check: scaling all the values of a given feature in the test set, such
as price to 2x, 3x, 4x etc. and observing changes in NDCG. We
found that the model’s performance was remarkably stable over
these values it had never seen before.
2. [ ] what NN structure ??
    1. [ ] trained with pairwise loss
2. toread
    1. [ ] Improving Deep Learning For Airbnb Search (industry, airbnb)
          
## Ref
