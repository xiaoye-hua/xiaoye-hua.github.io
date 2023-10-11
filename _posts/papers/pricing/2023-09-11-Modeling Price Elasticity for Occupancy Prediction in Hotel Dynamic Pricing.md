---
layout: post
title: 2022 - Modeling Price Elasticity for Occupancy Prediction Hotel Dynamic Pricing
published: True
date: 2023-09-11
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


1. Fliggy 

## Methods

1. Approach
   1. occupancy prediction
   2. revenue optimizaiton: apply a set of price, the find the max revenue
      1. Main contribution: 
         1. novel demand function that explicitly models the price elasticity of demand for occupancy prediction
         2. define a parameter to represent elaciticity; define formular in the NN
      2. 3 categories of features
         1. competiveness factors
         2. temporal factors
         3. characteristic factors
2. Online experiment
    1. a baseline manual pricing strategy
3. Business insight
   1. the occupancy of luxury hotels are less price-sensitive than budget hotels as they
have less substitutes in the market place
   2. For example, hot spring hotels are less price-sensitive in winter as the demand is seasonal.
   3. the features affecting 𝛽 are less dependent on price but more relevant to the room characteristics and external influences. 
## TODO & Questions & Further Reading
4. [ ] Evaluation metrics -> interesting 
    1. [ ] WMAPE
    2. [ ] why MAPE for classification problem 
5. [ ] reference paper reading