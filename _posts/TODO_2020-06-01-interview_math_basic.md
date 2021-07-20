---
layout: post
title: Interview Questions Notes
subtitle: Probability and Statistic Learning
date: 2020-06-01
published: False
mathjax: True
catalog: true
tags:
  - data structure & algorithms
  - interview
---
# TOC
1. Introduction
{:toc}

# Introduction
In this session, I'll take a note of the interview questions that I encountered. This post is about probability and statistic learning

# Two Players Toss Coins

## Questions

Two players alternatively toss a coin, what's the probability of wining by getting the first head for the first players?

First, define three events:

- A: the first player wins the game
- B: the second player wins the game
- C: the first player doesn't get head when tossing for the first time

## Approch One
We have the below equations:

- $P(A)+P(B)=1$
- $P(B\|C)=P(A)$
- $P(B\|C)=\frac{P(A)}{P(C)}$
- $P(C) = 0.5$

Then we get:

$P(A)=\frac{2}{3}$

## Approch Two

$P(A)$


