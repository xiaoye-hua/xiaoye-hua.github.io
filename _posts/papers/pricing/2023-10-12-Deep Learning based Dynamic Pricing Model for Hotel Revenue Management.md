---
layout: post
title: 2019 - Deep Learning based Dynamic Pricing Model for Hotel Revenue Management
published: True
date: 2023-10-12
mathjax: True
catalog: true
tags:
  - paper reading
  - Industry
  - Meituan
  - pricing
---

**Table of Contents**
1. Introduction
{:toc}

This work mainly focus the hotel.
		
## Problem Definition & Methods        

1. Objective: max revenue 
2. Main components
   1. get reasonable base rate
      1.  average value of its historical sales
   2. occupancy prediction
      1. model:
         1. input: data from previous 28day
         2. output: occupancy for the next 7 days
      2. Metric: MAPE
   3. dynamic pricing system to model human expertise
      1. Features
         1. base rate 
         2. predicted occupancy 
         3. other relating factors
      2. data 
         1. Assumption: We assume that the prices
of such samples are adjusted by hotel managers to increase
the revenue and the pricing strategy considering a variety of
situational factors can be transferred to other hotels.
         2. How: we select hotel samples of which the revenues in the period increase
compared with their revenues of previous periods, eg., last
week, last month or last year. 


# Contribution


1. occupancy prediciton model
2. dynamic pricing model



## TODO & Questions & Further Reading
