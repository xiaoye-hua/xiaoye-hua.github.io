---
layout: post
title: 2017-Search Ranking and Personalization at Airbnb
published: True
date: 2023-04-17
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

1. Problem definition: Airbnb
    1. two-sided marketplace
    2. user never book the same listing for twice
    3. a listing can only be booked by one guest at the same time
    4. tradeoff of guest and host preference
2. Principle offline metrics: NDCG


## Methods

1. Search components
    1. Retrieval of listing: location queries and broad queries
    2. Ranking
2. About user sessions
    1. label propagation backwords or forwards
3. Ranking model 
    1. Learning To Rank model
    2. Utility
        1. booked 1, rejected -0.4, impression, 0, clicked 0.01
4. Listing embedding
5. [ ] Query embedding -> used in type-ahead 

## TODO & Questions & Further Reading

1. [ ]  Dual Discount Curve Pairwise to push bad result bottom
