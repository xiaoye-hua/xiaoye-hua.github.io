---
layout: post
title: From Machine Learning to Deep Learning
subtitle: Deep Learning Explain Series (Part 1)
date: 2020-07-25
published: True
mathjax: True
catalog: true
tags:
  - deep learning explain series
  - machine learning
---
# TOC
1. Introduction
{:toc}

# Introduction
This post is part of Deep Learning Explain Series. 

## Why This Series?
When you are working as a data scientist or machine learning engineer, you will realize that you'll need to learn plenty of things: programming skills, git and CICD tools, math, machine learning or deep learing algorithms and so on. In addition, every day new machine learning techniques came out. It takes plenty of time for me to teach myself machine learning and deep learning from book, online courses and my colleagues. Since entering the data science field, I have constantly searched for methods about how to learn efficiently. 

Curently I really agree with the idea of "ten steps to learn" in the book [“Soft Skills — The Software Developer’s Life Manual”](https://book.douban.com/subject/26312275/). I really agree with the tenth steps: teach. About this steps, the author says: "when you go through this process, you'll find there are many thing you think you understand but you didn't. You will make connections that you didn't see before and simplied the the information in your head as you try to condense it down and regurgitate it... This step is crucial to retain information and developing more than a surface-understanding of a subject" 

This series of posts serves as a practice of the tenth steps: to take what you've learned from you mind and organize it in a way that other people can understand.

## How Will This Series be Structured?
This series will only explain the basic idea of supervised learning in DL. As a result, we'll ignore some unimportant details. The first post serves as a bedrock of this series: in this post, the difference between ML and DL, the key problem and toxonomy of ML will be explained. Through all this series, I'll refer to the first post sometimes.

After the first post, the following topics will be explained:
1. Linear neural network and multilayer perception
2. CNN
3. RNN
4. GNN

# Key Problem of ML or DL
When solving problem with machine learning, three steps will be taken:
1. Define a machine learning model 
2. Define the objective function
3. Optimize in order to maximize or minimize the objective functions

In terms of supervised learning, deep learning belongs to machine learning. However the deep learning model is more complex.

# Taxonomy of ML or DL
For supervised learning, ML can fall in to two categories: regression and classification.

The input for regression and classification are almost the same. However, the output is different: for regression problem, the output is  a number; for classification, the output is a specific category, which usually represented by one-hot encoding.

