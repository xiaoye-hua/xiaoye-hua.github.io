---
layout: post
title: Reinforcement Machine Learning Summary
date: 2021-09-13
published: False
mathjax: True
catalog: true
tags:
  - machine learning
  - reinforcement learning
  - summary 2021
---
# TOC
1. Introduction
{:toc}

# Tabular Solution Methods

## Multi-armed Bandit

1. Muti-armed Bandit method was used in the scenario where we're faced with multiple choice, we have to maximum the rewards by balancing exploration and exploitation.
2. Methods include:
    1. Action-value methods (Ref 1)
        1. greedy method
        2. $\epsion$ greedy
        3. Upper confidence bound
    2. Gradient bandit algorithm
    3. Contextual bandit algorithm
        1. Extension version of multi-armed bandit and simplified version of reinforcement learning (Ref 3)
        2. Compared to multi-armed bandit: take contextual information(e.g user preference) into consideration (Ref4)
        3. a online A/B testing for uplift, and every observation is a test. Compared to normal A/B testing, contextual multi-armed bandit can cope with a large number of treatments(Ref2)
    
# Ref
1. Reinforcement Learning - An Introduction 
2. [Multi-armed Bandit VS Uplift Model](https://app.yinxiang.com/fx/42e18a61-579e-4884-8b94-bd17a5853972x)
3. [Contextual Bandit and Reinforcement Learning](https://app.yinxiang.com/fx/ed280226-9f1a-42cb-9f29-387db5e673b3)
4. [What are Contextual Bandit? Is A/B testing dead?](https://app.yinxiang.com/fx/6d1bde4c-c500-4034-8627-e4790e966dcc)