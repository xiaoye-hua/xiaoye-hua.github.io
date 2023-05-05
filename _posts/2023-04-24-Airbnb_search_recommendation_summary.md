---
layout: post
title: Airbnb
published: False
date: 2023-04-23
mathjax: True
catalog: true
tags:
  - RecSys
  - Industry
  - Airbnb
---

**Table of Contents**
1. Introduction
{:toc}

# Introduction

The first 2 sections will focus more on business and in the third section, detailed of ML solution will be presented

# Problem Definition

1. Objectives are set to focus bookings, hoping the increase of booking will bring the increase of revenue. And it works in their cases.
    1.prioritizing listings that are appealing to the guest but at the same time demoting listings that would likely reject the guest
2. Key metrics are bookings and revenue. 
3. Solution consists of 2 stages
    1. Retrieve (or candidiate generation):  location queries and broad queries
    2. Rank
    3. several models in the system: ese include models that predict
the likelihood of a host accepting the guest’s request for booking,
models that predict the probability the guest will rate the on trip
## Unique Search Ranking at AirBnb

1. two-sided marketplace
2. user never book the same listing for twice
3. a listing can only be booked by one guest at the same time
4. tradeoff of guest and host preference
5. Arguably, content discovery and search ranking
for these types of marketplaces needs to satisfy both supply and
demand sides of the ecosystem in order to grow and prosper.


# Lesson Learned


1. session-based will important for login users


# Evolution & Impacts Summary

Refer to spreadsheet

# Model Evolution

How do we iterate -> img

## Metrics

1. NDCG
2. Value assignment

## Training Data

1. [ ] a session
2. [ ] 

## Model details

### Tree-based 

### From Tree-based to NN

### DNN

1. Hotel embedding 
    1. some changes
2. Benifit
    1. Earlier
the focus was largely on feature engineering, but aer the move to
deep learning, trying to do beer math on the features manually
has lost its luster. is has freed us up to investigate problems at a
higher level, like how can we improve our optimization objective,
and are we accurately representing all our users?

### Next Step


# References

1. 2017
    1. [Search Ranking and Personalization at Airbnb](https://dl.acm.org/doi/abs/10.1145/3109859.3109920)
2. 2018
    1. [Applying Deep Learning To Airbnb Search](https://arxiv.org/pdf/1810.09591.pdf)
    2. [Real-time Personalization using Embeddings for Search Ranking at Airbnb](https://www.kdd.org/kdd2018/accepted-papers/view/real-time-personalization-using-embeddings-for-search-ranking-at-airbnb)
2. 2020
    1. [Improving Deep Learning For Airbnb Search](https://arxiv.org/pdf/2002.05515.pdf)
    
# TODO

1. [ ] [to check](https://scholar.google.com/citations?hl=en&user=agONEw4AAAAJ&view_op=list_works&sortby=pubdate)
