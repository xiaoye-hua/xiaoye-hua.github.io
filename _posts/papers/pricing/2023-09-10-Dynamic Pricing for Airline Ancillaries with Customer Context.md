---
layout: post
title: 2019 - Dynamic Pricing for Airline Ancillaries with Customer Context
published: True
date: 2023-09-10
mathjax: True
catalog: true
tags:
  - paper reading
  - Industry
  - pricing
---

**Table of Contents**
1. Introduction
{:toc}
		
## Problem Definition

1. Problem: dynamic pricing for airline ancillaries with customer context 
2. Objective: Revenue & conversion

## Methods & Contribution

1. Approach: 2 components
   1. purchase probability model
   2. revenue optimization model: given the purchase probability, recommend the optimal price that maximizes the expected revenue
2. Model 
    1. a two-stage 
       1. purchase probability prediction
       2. Since price are within a range due business constrains -> map purchase probabilty to price
    2. a two-stage model 
       1. uses a deep neural network for forecasting
       2. coupled with a revenue maximization technique using discrete exhaustive search (define several pecentage beforhands)
    3. a single-stage end-to-end deep neural network that recommends the optimal price with customized loss function
3. Result 
    1. We show that traditional machine learning techniques outperform human rule-based approaches in an online setting by improving conversion by 36% and revenue per offer by 10%.
4. Contribution
   1. dynamic pricing using user specific info without violate customer privacy


## TODO & Questions & Further Reading

1. [ ] related work part 
2. [ ] customized loss function for 3rd approach
3. borrowed offline metrics from Airbnb paper 

