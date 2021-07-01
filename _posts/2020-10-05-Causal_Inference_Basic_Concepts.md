---
layout: post
title: Casual Inference Basic Concepts
date: 2020-10-05
published: True
mathjax: True
catalog: true
tags:
  - machine learning
  - causal inference
---
# TOC
1. Introduction
{:toc}

# Methodolegy

## Causal Inference
为什么需要因果推断： 相关性并不意味着因果关系。比如游戏公司在AB实验组中，营销组的登录比较高，如何判断高登录率多大程度是营销导致的，多大程度是因为用户本身就是高活用户给。本质上，我们在分析一个干预（treatment）对结果（outcome）的影响。

常见的因果推断模型有两个：
1. Potential Outcome Framework (Robin Causal Model (RCM))
2. Causal diagram

## ATE, CATE, and ITE
Difference between ATE and CATE:
1. ATE: average treatment effect of a treatment or prevention
2. CATE (similar to individul treatment effect ITE): ATE at the indiidual or segment level 

ATE Wikipedia:
![b4e5dacce0346354a94701b4f6df2d28.png](evernotecid://665CD574-A4AA-4D10-8D15-0D4660C8F018/appyinxiangcom/12900596/ENResource/p3614)



## Propensity Score： Estimation & Matching

要解决的问题：在分析和实验中，我们要比较的两个人群不同质，无法进行比较

目的：消除观察性实验中 实验组和对照组的不同质，进而得到因果效应的估算

倾向性得分的本质：一个用户属于实验组的"倾向性得分"

倾向性得分匹配的本质：我们对每一个实验组用户都在对照组里匹配一个得分相等（要求有点严苛）的用户，我们就能得到同质的实验组和对照组，就可以假装我们做了一个 A/B Test 了，接着就可以随意地进行组间比较了

### Ref

[因果推断漫谈（二）：倾向性得分匹配介绍](https://dango.rocks/blog/2019/01/20/Causal-Inference-Introduction2-Propensity-Score-Matching/)

## Synthetic Data

we generate data with known causal and non-causal links between the outcome, treatment and some of confounding variables.

Refer to Validate with synthetic data set for more details

## Sensitivity Analysis

Sensitivy analysis aim to check the robustness of the unconfoundeness assumption. If there is hidden bias (unobserved confounders), it detemineds how severe whould have to be to change conclusion by examine the average treatment effect estimation

## Uplift Model
### Meta-Learner Algorithm
### Tree-Based Algorithm
### Offline Evaluation
1. Qini metirc
2. ERUPT (Expected Respond Under Proposed Treatments. refer to MR-uplift Python package)
    1. Advantages compared to Qini: applied to multiple treatments

### Python Package
#### CausalML
#### MR-uplift
MR-uplift:

1. support for multiple response
    1. 单个response到多个reponses：objective funcion转化： $\pi(x_i) \rightarrow \pi(x_i, W)$ (Refer to [Estimating and Visualizing Business Tradeoffs in Uplift Models](https://medium.com/building-ibotta/estimating-and-visualizing-business-tradeoffs-in-uplift-models-80ff845a5698) for details)
    2. 加入weights 后, ERUPT 定义也发生变化.These estimate the tradeoffs by applying various weights to each of the predictedresponses and calculating the corresponding expected responses. For example, suppose we have have a weight β and objective function $\beta*revenue-(1-\beta)*costs$. A weight of β=1 corresponds to revenue maximization, β=0 costminimization, and β=.5 to be profit maximization.
2. How to decide whether we should assign? ——> 使 y 最大的t
3. 和一般的角度不同，MR-uplift把无treatment也当成一种treatment，所以问题转化为最大化y，而不是最大化$y_{t_1} -y_{t_0}$
4. OOS data: Out Of Sample data
5. MR-Uplift uses a multi-output neural network with a mean-squared error loss. (KerasRegressor loss function: MSE)

**TODO**
2. [Reference blogs to read](https://github.com/Ibotta/mr_uplift)
2. ERUPT curve 如何计算？ 有求差么？?? 没看懂啊？？
    1. fit() 里 t (np array or pd.dataframe): Treatment Variables of shape num_observations by num_treatment columns ？？
    3. uplift_model.get_erupt_curves()输出中 weight 和 treatment 里面的-1是啥意思？
6. [variable importance metrics？？(code example)](https://github.com/Ibotta/mr_uplift/blob/master/examples/mr_uplift_variable_importance_example.ipynb)
7. [new oprimized loss (code example)](https://github.com/Ibotta/mr_uplift/blob/master/examples/mr_uplift_new_optimized_loss.ipynb)
10. Uplift for user retention


# Reference
1. [CausalML: Python Package for Causal Machine Learning - Paper with code](https://ml.paperswithcode.com/paper/causalml-python-package-for-causal-machine)
2. [因果推断漫谈（一）掀开因果推断的面纱](https://dango.rocks/blog/2019/01/08/Causal-Inference-Introduction1/)
3. [因果推断漫谈（二）：倾向性得分匹配介绍](https://dango.rocks/blog/2019/01/20/Causal-Inference-Introduction2-Propensity-Score-Matching/)
4. [MR-uplift Python package](https://github.com/Ibotta/mr_uplift)
2. [Definition of ERUPT](https://medium.com/building-ibotta/erupt-expected-response-under-proposed-treatments-ff7dd45c84b4) 
3. [ICE: Individual Conditional Expectations](https://arxiv.org/pdf/1309.6392.pdf)


# TODO
1. [2021年了， 机器/深度学习还有哪些坑比较能好挖？ - 苘郁蓁的回答 - 知乎](https://www.zhihu.com/question/440538267/answer/1695274083)


