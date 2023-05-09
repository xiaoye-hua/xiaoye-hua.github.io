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

## Metrics

1. Offline
    1. NDCG
2. Online
    1. booking & booking value
    2. revenue
    3. Engagement metrics: listing viewed; listing saved
    
## Problem, Solution & Impact

Refer to spreadsheet

# Solutions in Details

## Overview - How do they iterate?

How do we iterate -> img

## Tree-based Model

1. Assign labels to different feedback
2. Two ways of training: point-wise and pair-wise training

### GBM Regression Model (2015)

1. Point-wise training
2. Loss: RMSE (??)

### GBDT Ranker (2017)

1. Pair-wise training
2. Within the same search session, generate listing pairs. (img needed)
3. Loss: cross entropy
4. Special modifications
    1. [ ] weighted pairwise
    2. [ ] Dual discount curve pairwise

## Path to DL model ()

Benifit of DL:Benifit
    1. Earlier
the focus was largely on feature engineering, but aer the move to
deep learning, trying to do beer math on the features manually
has lost its luster. is has freed us up to investigate problems at a
higher level, like how can we improve our optimization objective,
and are we accurately representing all our users?

### Hotel Embedding & Query Embedding (2018) 

#### Hotel Embedding

1. Based on users search session and skip-gram(w2v), get listing embedding
2. (hotel_embedding img)
3. Special modifications
    1. Better negative-sampling: instead of sampling globally, sample negative listings from the same city
    2. More weight to booked listings: in the booking sessions, the booking list will always be the context listing
    3. [ ] more??

#### Query Embedding

1. How it work (img)
2. Example (img)
3. More details, for example negative sampling 


### Simple NN

1. simple single hidden layer NN with 32 fully connected ReLU
activations
2. Features: Same features as GBDT
3. Loss: L2 regresson loss 
4. Target: 1 -> booking; 0 -> not booking
5. Performance: -> neutral bookings as GBDT

### Lambdarank NN

1. Pair-wise NN
2. Loss: cross entropy
3. Target: same as previous model 
2. [ ] Special changes
    1. weighted NDCG
    
    
### NN model with features from GBDT and FM

1. Production model is NN. For the FM model we took the nal prediction
as a feature into the NN. From the GBDT model, we took the index
of the leaf node activated per tree as a categorical feature. A factorization machine (FM) [14] model that predicted the
booking probability of a listing given a query, by mapping
listings and queries to a 32-dimensional space.
2. Structure (img)


### Deep NN

1. We were able to deprecate all that complexity by
simply scaling the training data 10x and moving to a DNN with 2
hidden layers.
2. Some special features
    1.  Exceptions include
features output from another model:Price of listings that have the Smart Pricing feature enabled,
supplied by a specialized model; Similarity of the listing to the past views of the user, computed based on co-view embeddings [9].

3. Failed models
    1. (todo)


## Improve DL



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

## Diversity 

Instead of building a single model, build models for each position

1. Position 0: reuse the regular pairwise model 
2. From position 1 to N: model has addition input which is the listing from position 0 to position N-1

## Lessons Learned

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
2. [ ] medium articles
3. [ ] Airbnb category

# Others 

1. several models in the system: ese include models that predict
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


## Training Data

1. [ ] combined sessions from 2017 papers
2. [ ] selected sessions for 2023 diversity papers