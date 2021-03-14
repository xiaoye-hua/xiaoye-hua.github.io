---
layout: post
title: Policy Gradient
subtitle: Deep Reinforcement Learning Course Note (Part 2)
date: 2020-05-23
published: False
mathjax: True
catalog: true
tags:
  - deep reinforcement learning
  - machine learning
  - 学习笔记-course note
---
# TOC
1. Introduction
{:toc}

# Introduction
This is the course summaries of UC Berkeley CS285 deep reinforcement learning. From the goal of reinforcement learning, we can derive policy gradient methods. However, it suffers the problems of high variance. In order to solve this problem, causality and baselines methods are used. Gradient policy methods is a type of on-policy methods, which is a special case of off-policy learning.

# From the Goal of RL to Policy Gradient

# Variance Reduction Methods for Policy Gradient 

# On-policy VS off-policy
All learning control methods faces an **dilemma**: they seek to learn action values conditional on the subsequent optimal behavior, but they need to behavior un-optimal in order to explore all actions. How can we learn optimal action while according to exploratory policy ?
1. On-policy learning is a compromise: to learn the optimal from the sub-optimal behavior, 
    1. simple and considered first
    2. great variance and slow to converge
2. while for off-policy, there are two policy: target policy is the policy that it will learn, and the behavior policy is used to generate policy.
    1. requires additional concepts and notations
    2. more powerful and general 


# Reference
1. [UC Berkeley CS285: Deep Reinforcement Learning, Decision Making, and Control](http://rail.eecs.berkeley.edu/deeprlcourse/)
2. 