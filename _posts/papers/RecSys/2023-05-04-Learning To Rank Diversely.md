---
layout: post
title: 2023- Learning To Rank Diversely
published: True
date: 2023-05-04
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

1. Prove the following assumption is wrong: the booking probability of a listing could be
determined independently of other listings in search results.
2. Key metrics: NDCG
3. About affordabilityleaning and quality: we can apply the
broad classification that the majority ∼80% of users are affordabilityleaning. The remaining minority ∼20% are quality-leaning

## Methods

1. Previous methods
    1. check section 6
2. Current methods
    1. model for each position considering previous listings 

## Impact

1. NDCG
    1. Offline: +0.45%
    2. Online: +1.5%
2. Booking & booking value: 0.29% in booking and 0.8% in booking value (it means it mainly influence high value booking, right??)
    1. mainly come from first time user 
3. Engagement: 0.46% list views; 1.1% in list saved
4. Position utilization
    1. the utilization
of the top position increased significantly, followed by some gain
for the second position


## TODO & Questions & Further Reading

1. [ ] paper: Managing Diversity in Airbnb Search
2. [x] re-visit introduction section -> summary needed

