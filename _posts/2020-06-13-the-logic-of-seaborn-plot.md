---
layout: post
title: The Logic Behind Seaborn
<!-- subtitle:  Reinforcement Learning Basic - Concepts and Taxonomy -->
date: 2020-06-13
published: True
mathjax: True
catalog: true
tags:
  - machine learning
---
# TOC
1. Introduction
{:toc}

# Introduction
Seaborn is a Python package to make statistical graph. It's built on matplotlib and is closely intergrated with pandas package. Of course, we don't need to know it's design logic in order to use it. However, if we know the design logic behind seaborn, it'll be easy to find a visualization solution with seaborn when facing a problem.


# The Logic

There are four types of "figure-level" functions in seaborn which are: sns.relplot(), sns.catplot(), sns.joinplot() and sns.pairplot(). These high level functions are building on two basic categories of functions: 'axes-level' functions and axes grids. Below is a mind-mapping of these logic:

<img src='/img/Seaborn.png' width="900">

# Reference
1. [An Introduction to Seaborn](https://seaborn.pydata.org/introduction.html)
2. [Official Seaborn Toturial](https://seaborn.pydata.org/tutorial.html)