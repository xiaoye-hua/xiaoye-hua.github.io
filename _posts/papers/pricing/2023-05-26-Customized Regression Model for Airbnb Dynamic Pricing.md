---
layout: post
title: 2018 - Customized Regression Model for Airbnb Dynamic Pricing
published: True
date: 2023-05-26
mathjax: True
catalog: true
tags:
  - paper reading
  - Industry
  - Airbnb
  - pricing
---

**Table of Contents**
1. Introduction
{:toc}
		
## Problem Definition

1. Objective
    1. help hosts set optimal prices for their listings
2. Uniqueness of this problem at Airbnb
    1. no identical product at Airbnb
3. Product
    1. Three components in the solution. Mainly focus on the 2nd component: regression model predicting the optimal price 
    2. 2 products: smart pricing tools and price tool
3. Contributions
    1. Regression model with customized loss function
    2. a set of offline evaluation metrics -> interesting and helpful

## Methods

1. previous or existing methods
    1. revenue maximization pricing strategies
        1. By tracking how demand varies with respect to price for a large number of identical products, a demand curve F (P) can be estimated, which determines demand as a function of price P. Then the problem of revenue maximization is to find the price P that yields maximal P×F (P). The key to the success of this approach is to get an accurate estimation of the demand function F (P) 
            1. -> not work at Airbnb because there is no identical listing
2. Unique challenges at Airbnb
    1. demand estimation
    2. Partial price adoption from hosts
2. Current methods
    1. Three components
        1. Booking probability estimation
        2. Strategy model (regression model)
        3. Personalization 
   
## Impact

1. The launch of the first iteration of the
strategy model yielded significant gains on bookings and booking
values for hosts who have adopted our suggestions


## TODO & Questions & Further Reading

1. [ ] the 3rd component -> dig into

