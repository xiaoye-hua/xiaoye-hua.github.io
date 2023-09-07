---
layout: post
title: GPT Papers
subtitle: From GPT to GPT4
published: True
date: 2020-09-06
mathjax: True
catalog: true
tags:
  - paper reading
  - LLM 
---

**Table of Contents**
1. Introduction
{:toc}

It's time to go through GPT papers. 


1. Improving Language Understanding by Generative Pre-Training (GPT 2018)
    1. Problem:Although large unlabeled text corpora are abundant, labeled data for learning these specific tasks is scarce, making it challenging for discriminatively trained models to perform adequately.
    2. Main contribution: generative pre-training on unlabeled data + discriminative fine-tuning on specific task
    3. Result: Our general task-agnostic model outperforms discriminatively trained models that employ architectures specifically crafted for each task, significantly improving upon the state of the art in 9 out of the 12 tasks studied.
2. Language Models are Unsupervised Multitask Learners (GPT2 2019)
    1. Problem: 
    2. Main changes
        1. more data
        2. zero-shot setting
    3. Result:. Our largest model, GPT-2, is a 1.5B parameter Transformer that achieves state of the art results on 7 out of 8 tested language modeling datasets in a zero-shot setting but still underfits WebText
3. Language Models are Few-Shot Learners (GPT3 2020)
    1. Main changes: 
        1. For all tasks, GPT-3 is applied without any gradient updates or fine-tuning, with tasks and few-shot demonstrations specified purely via text interaction with the model.
        2. we train GPT-3, an autoregressive language model with 175 billion parameters, 10x more than any previous nonsparse language model, and test its performance in the few-shot setting.

## TODO & Questions & Further Reading
[ ] GPT4 report

## Ref
1. [GPT 论文精读 - Mu Li](https://www.youtube.com/watch?v=t70Bl3w7bxY)
