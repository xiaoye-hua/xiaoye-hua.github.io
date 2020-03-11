---
layout: post
title: Machine Learning Algorithms Summary
# subtitle:  Neutron Network and Deep Learning
date: 2017-11-30
published: True
mathjax: True
catalog: true
tags:
  - machine learning
---
## TOC
1. Introduction
{:toc}

# Introduction
在此总结传统机器学习算法，主要有：

一. 监督学习(Supervised Learning):
1. 线性回归(Linear Regression)
2. 逻辑回归(Logistic Regression Classifier)
3. 最近紧邻法(K-nearest Neighbors)
4. 决策树(Decision Tree)
5. 随机森林(Random Forest)
6. 支持向量机(Support Vector Machine)
7. 朴素贝叶斯(Naive Bayes)

二. 非监督学习(Unsupervised Learning):
1. K-平均聚类(k-means-clustering)



# 监督学习

监督学习：训练时用label data.
问题主要分为两类：
<ol>
<li>回归问题(Regression)</li>
<li>分类问题(Classification)</li>
</ol>

## 线性回归

**Linear regression adopts a linear approch to model the relationship between dependent variable(target) and one or several independent variable (predictor)**

  线性回归为最简单的回归问题，运用线性预测模型来建模。

  定义残差平方和RSS(Residual Sum of Square )如下：
  $$RSS = \sum_{i}(y_{true}-y_{predict})^2$$
  计算方法为：Ordinary least square 直接求解; 梯度下降迭代求解。

  算法：
  - Given X, want $y_{predict}$,
  - Param $w=R^{n}$, $b\in R$
  - Output: $y_{predict}=w^Tt + b$

  如下图：

<img src='/img/deep_learning_course/lr.png' width="400">

## 逻辑回归

**One of classification algorithms, actually single layer neural network with sigmoid function as activation function**

  通常用于二元分类(Binary Classification),可理解为一层的神经网络系统。

  算法：
  - Given X, want $y_{predict}$,
  - Param $w=R^n$, $b\in R$
  - Output: $y_{predict} = \sigma(w^Tt +b)$ where $\sigma(z) = \frac{1}{1 + e^{-z}}$




  Loss function(single sample):
  - $L(y', y)=-(ylog(y') + (1-y)log(1-y'))$


  Cost function(entir train set):
  - $J(w, b) = \frac{1}{m}\sum_{i=1}^{n}L(y'^{(i)}, y^{(i)})$


  计算方法：
  - 梯度下降法


  对于Multiclass classification 问题： one-over-many approach

## 最近紧邻法 (KNN)

**Explain**
1. one of supervised learning both for classfication and regression, simplely remember all of training data(possible strored into a fast indexing structure such ball tree or KD tree)
2. Process
    1. calculate the Euclidean distance between the query and all training data
    2. get K nearest neighbers
    3. for classification, vote for the most frequent labels; for regression, average the labels
2. pros:
    1. easy, no need to build model; althoug simple, success in large number of problems such as handwritten digits and satellite image scenes
3. cons:
    1. become slow when number of training data increase

## 决策树

**Explain**
1. Used both for classfication and regression. Model behaves with "if this then that" conditions until yield the final result
2. Use creteria such as information gain or entropy to decide where to split the node
3. In terms of classification, the majority of labels from the child nodes are selected as result; in case of regression, average of labels of the child nodes are selected as result
4. Pros: easy to understand; no need to process data beforehead; no need to know the distribution of the data
5. Cons: tend to overfit

可用于回归和分类问题。

通过计算信息论中的信息熵(entropy), 进而计算出信息所得(infomation gain)来决定信息树的分叉。即通过计算所能得到的最高信息所得，来决定树节点的分割。

优点：
感念简单，可解释性强，输出结果容易理解．

缺点：过拟合，信息确实处理起来比较困难

## 随机森林

**Explain**
1. ensemble learning by combning serveral decision tree using bagging
2. it reduces variance
3. several decision trees are creating using sampling: every tree select subset of the datasets or subsets of all the features. Their results will be averaged as the final result.

Difference between random forest classifer and random forest regressor in sklearn:
1. split criterion for classifer: gini or infomation gain
2. split criterion for regressor: MSE or MAE

随机森林是多个决策树的合体(ensemble of decision tree), 即通过向决策树中引入方差使整体得到一个更好的结果。集成算法，随机选取不同特征和训练样本，生成大量决策树．准确性提高．

主要有两种方法：
- Bagging (subset of data)
- random features subset


应用场景：数据维度相对较低，对准确度有较高要求
### Decision Tree
There are three steps in this method
1. Selection of split feature
  2. classification criterion
    3. infomation gain(entropy)
    4. Gini coefficiency
  3. regression criterion
    4. MAE
    5. MSE
2. Creation of decision trees
3. Tree prune
  4. By minimize loss functions(cost function)

Three type of algorithms
1. ID3
2. C4.5
2. CART(classification and regression tree)



## 支持向量机 (Support Vector Machine)

**Explain**
1. supervised learning which is commonly use for classification
3. Goal is to find the the hyperplane that have the greatest margin between the hyperplane and the train datasets. it will make sure all the data are correctly classfied. If no hyperplane, the datasets will be mapped into higher dimension with kernel triks to find the hyperplane
4. Concepts explain
    1. support vector: the points that are close to the hyperplane, which, if removed, would alter the position of
        hyperplane. they are critical elements in the datasets
    3. kernel triks:
5. Pros: accuracy;
6. Cons: less effective on noiser data with ovelaping classes.
7. Usage: text classification

## 朴素贝叶斯(Naive Bayes Classifier)

**Explain**
1. a collection of algorithms that based on Bayes Theorem. based on the "naive" assumption of conditional independence of every pairs of features given the value of the target variable, which means that every feature contributes independently to the target variable
2. There different kinds of naive bayes classfier, they differ mainly by the assumptions they make regarding the distribution of $P(x_i/y)$
  3. Gaussian naive Bayes
  4. Multinormial naive Bayes
  5. Bernoulli naive Bayes
  6. cagegory naive Bayes
  7. ...
2. Pros: relatively simple; easy to train; run fast
3. Cons: In real case, features are not all independent
4. Usage: document classification and text spam detection

**Bayes Theorem**
1. $$P(A/B)P(B) = P(B/A)P(A)$$
   $$P(A/B) = \frac{P(B/A)P(A)}{P(B)}$$

# Unsupervised Learning

## K-means

**Explain**
1. Unsupervised learning
2. Process:
    1. Specify the desired number of clusters K
    2. Assign every observation randomly to 1 to K cluster
    3. Iterate until the cluster centroid stop changing
        2. Calculate the centroid of each cluster (centroid is the vector of the all features means for the observations in the kth cluster)
        2. assign each observation to the cluster whose centroid is closest (Euclidean Distance)
3. Pros:
4. Cons:
    1. likely end up in a local optimum, several runs with independent init might be necessary
