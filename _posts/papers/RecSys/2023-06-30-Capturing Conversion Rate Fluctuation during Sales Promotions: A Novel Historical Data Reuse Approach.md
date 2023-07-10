---
layout: post
title: 2023-Capturing Conversion Rate Fluctuation during Sales Promotions: A Novel Historical Data Reuse Approach
published: True
date: 2023-06-30
mathjax: True
catalog: true
tags:
  - paper reading
  - RecSys
  - Industry
  - Alibaba
---

**Table of Contents**
1. Introduction
{:toc}
		
## Problem Definition

1. Problem: CVR prediction problem during sales promotions during which there is a data drift
2. Objective: RPM and CVR

## Methods

1. HDR (Historical Data Reuse), three components
   1. Automated data retrieval module
      1. represents each promo as a vector
      2. based on nearest neighbor, find the one
   2. Distribution shift correction module (to address the disparity of the conversion behavior between the retireved promos and target promos)
   3. TransBlock module
      1. fine-tune model with historical data

## Impact

1. improve both ranking and calibration metrics
   1. ranking metric: AUC 
   2. Calibration metrics: 
      1. logloss
      2. ECE: Expected Calibration Error 
      3. PCOC: predicted CVR Over the Actual CVR
2. a lift of 9% RPM(Revenue Per Mille) and 16% CVR in Double 11 sales in 2022

## Next Step

1. Conversion differs between 
   1. weekdays and weekends
   2. begin and end of month
2. Utilize the data from other scenes

## TODO & Questions & Further Reading

[ ] definition of ECE, PCOC
[ ] to read: CTR, CVR papers (introduction section)
[ ] one epoch problem

