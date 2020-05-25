---
layout: post
title: Deep Reinforcement Learning Course Note (Part 1)
subtitle:  Supervised Learning of Behaviors - Imitation Learning
date: 2020-05-13
published: True
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
This is the course notes of UC Berkeley CS285 deep reinforcement learning.

# Intuition, Definition and Notation

Instead of learning from sparse rewards or specifying a manually reward function, the agent learns the optimal policy by learning, imitating the demonstrations of the experts.

Below shows the process:

<img src='/img/DRL/imitation_learning_notation.png' width="600">

Notations:
1. $s_t$ state of the environment at time t
2. $o_t$ observation of the agent at time t
3. $a_t$ action of agent at time t
4. ${\pi}_{\theta}(a_t \| o_t)$: policy
5. ${\pi}_{\theta}(a_t \| s_t)$: policy(if fully observed)
6. $p(s_{t+1}\|a_t, s_t)$: transiton fuctions to $s_{t+1}$ given $a_t$ and $s_t$


# Algorithms

|              Type              |                        Advantage                        |               Disadvantage               |                                            Use When                                           |
|:------------------------------:|:-------------------------------------------------------:|:----------------------------------------:|:---------------------------------------------------------------------------------------------:|
|        Behavior Cloning        |                          simple                         |  no long-term planing  error can add up  |                                   the application is simple                                   |
|     Direct Policy Learning     |                    long-term planing                    | interavtive expert demonstrations needed |                 application is complex; interactive demonstration is available                |
| Inverse Reinforcement Learning | long-term planing no need for interavtive demenstration |           can be hard to train           | interavtive demonstartion is no available; easier to learn reward function then expert policy |

## Behavior Cloning

Definition: learning the expert's policy with supervised learning. 


## Direct Policy Learning (by interactive demonstrator)

Definition: behavior cloning is a special of direct policy learning. First, supervised learning, then we roll out the game with the expert, and collect data. After that, we get more data demonstrated by the experts. Then go through the loop again. 

<img src='/img/DRL/IL.png' width="400">

In the process of learning, the agent should 'remembers' all the mistakes that made. Two approches are used:
1. Data aggregation: agents are trained with all the history training data
2. Policy aggregation: agents are only trained with data from the last iteration and then combined with policy from previous rounds wiht geometric blending.

## Inverse Reinforcement Learning

Definition: learn the reward function from the expert demonstrations, the train the agent with RL algorithms.

Procedures are as follows:

<img src='/img/DRL/process_of_IRL.png' width="400">

Two type of IRL: model-free and model-given
<img src='/img/DRL/type_of_IRL.png' width="400">


# Applications

1. Game AI
2. Structured prediction
3. etc..

Refer to [imitation learning tutorial ICML 2018 video](https://www.bilibili.com/video/BV1eb411a7qP?from=search&seid=11615249243079680566) for more application practices


# Reference
1. [UC Berkeley CS285: Deep Reinforcement Learning, Decision Making, and Control](http://rail.eecs.berkeley.edu/deeprlcourse/)
2. [A Brif Review of Imitation Learning](https://medium.com/@SmartLabAI/a-brief-overview-of-imitation-learning-8a8a75c44a9c)
2. [imitation learning tutorial ICML 2018](https://www.bilibili.com/video/BV1eb411a7qP?from=search&seid=11615249243079680566)
4. [模仿学习介绍](https://zhuanlan.zhihu.com/p/25688750)