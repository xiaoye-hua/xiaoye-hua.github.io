---
layout: post
title: The Logic Behind Matplotlib & Seaborn
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

# Matplotlib
Notes about two types of interface:

1. Object-Oriented API: this module utilzes the instance of axes.Axes to render the visualization on the instance of figure.Figure.
2. State-based interface - Pyplot: this module is based on MATLAB, and this module is encapsulated within the matplotlib.pyplot module.

Two things to keep in mind:

1. Axes represents a individual plot
2. Figure is the final image which can contain one or more Axes.

# Seaborn

There are four types of "figure-level" functions in seaborn which are: sns.relplot(), sns.catplot(), sns.joinplot() and sns.pairplot(). These high level functions are building on two basic categories of functions: 'axes-level' functions and axes grids. Below is a mind-mapping of these logic:

<img src='/img/Seaborn.png' width="900">

# Reference
1. [Matplotlib Official Cheatsheets](https://github.com/matplotlib/cheatsheets#cheatsheets)
2. [Matplotlib Object-oriented API VS Pyplot](https://matplotlib.org/stable/tutorials/introductory/lifecycle.html#combining-multiple-visualizations)
2. [Official Seaborn Toturial](https://seaborn.pydata.org/tutorial.html)
3. [Overviews of Seaborn Functions](https://seaborn.pydata.org/tutorial/function_overview.html)
1. [An Introduction to Seaborn](https://seaborn.pydata.org/introduction.html)
