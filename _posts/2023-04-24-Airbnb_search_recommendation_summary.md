---
layout: post
title: Search and Recommendation in Airbnb from 2015 to 2023
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

1. **Objectives** are set to focus bookings, hoping the increase of booking will bring the increase of revenue. The objective doesn't change until now.
    1.prioritizing listings that are appealing to the guest but at the same time demoting listings that would likely reject the guest
2. Strategy to optimize the above objective: 
    1. 1st stage: treat every listing independently and assume that the booking probability of a listing could be
determined independently of other listings in search results.
    2. 2nd stage (after 2020): treat the all listings as one; try to diverse the result
2. Key metrics are bookings and revenue.
3. Solution consists of 2 stages
    1. Retrieve (or candidiate generation):  location queries and broad queries
    2. Rank


# Evolution & Impacts Summary

Refer to spreadsheet



## Unique Search Ranking at AirBnb
1. two-sided marketplace
2. user never book the same listing for twice
3. a listing can only be booked by one guest at the same time
4. tradeoff of guest and host preference
5. Arguably, content discovery and search ranking
for these types of marketplaces needs to satisfy both supply and
demand sides of the ecosystem in order to grow and prosper.

## Metrics

1. Offline
    1. NDCG
2. Online
    1. booking & booking value
    2. revenue
    3. Engagement metrics: listing viewed; listing saved


# Model Evolution

How do we iterate -> img

## Metrics

1. NDCG
2. Value assignment

## Training Data

1. [ ] combined sessions from 2017 papers
2. [ ] selected sessions for 2023 diversity papers

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

# Lesson Learned

1. session-based will important for login users
2. Example of success iterations from 2017 papers


### Next Step

Search and recommendation from 

1. booking.com
2. Agoda
3. ... 

# References

1. 2017
    1. [Search Ranking and Personalization at Airbnb](https://dl.acm.org/doi/abs/10.1145/3109859.3109920)
2. 2018
    1. [Applying Deep Learning To Airbnb Search](https://arxiv.org/pdf/1810.09591.pdf)
    2. [Real-time Personalization using Embeddings for Search Ranking at Airbnb](https://www.kdd.org/kdd2018/accepted-papers/view/real-time-personalization-using-embeddings-for-search-ranking-at-airbnb)
2. 2020
    1. [Improving Deep Learning For Airbnb Search](https://arxiv.org/pdf/2002.05515.pdf)
3. 2023
    1. [Learning To Rank Diversely](https://arxiv.org/pdf/2210.07774.pdf)
    
# TODO

1. [ ] [to check](https://scholar.google.com/citations?hl=en&user=agONEw4AAAAJ&view_op=list_works&sortby=pubdate)

# Others 

1. several models in the system: ese include models that predict
the likelihood of a host accepting the guest’s request for booking,
models that predict the probability the guest will rate the on trip