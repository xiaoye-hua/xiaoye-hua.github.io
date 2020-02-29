---
layout: post
title: "Boosting algorithms"
subtitle:
date: 2019-01-22
published: True
tags:
  - machine learning
  - xgboost
  - lightGBM
---

# Ensembling
**boosting VS bagging**
1. bagging 为放回抽样，多数表决或者平均 (Random Forest)
2. 树的集成本质上为boosting, boosting的实质是加性模型 (GBDT)
3. boosting 下一棵树依赖上一棵树的训练, 树树之间只能串行
# Boosting
## Definition
**Families of algorithms which convert weak learners to strong learners**


## 步骤：
1. 初始：第一个弱学习机，所有点都初始化权重相同，预测
2. 过程：增加上一个学习机被预测错的点的权重，减少预测对的点的权重，进行下一个弱学习机
3. 整合：根据所有弱学习机的精度来决定各个模型的权重，整合结果


几种算法:
1. AdaBoost (Adaptive Boosting)
2. GBDT (Gradient Boosting Decision Tree)
  1. 之前使用的是普通决策树(Desicion Trees), GBDT第一次引入了回归树CART(Classfication And Regression Trees)
一阶泰勒展开
3. XGBoost
  1. 相比GBDT, 显式引入正则项,约束决策树的复杂性
  2. 二阶泰勒展开
  3. 支持列抽样, 防止过拟合(与RF一样)

## XGBoost (eXtreme Gradient Boosting)
### 参数分类：
1. General Parameters: Guide the overall functioning
2. Booster Parameters: Guide the individual booster (tree/regression) at each step
3. Learning Task Parameters: Guide the optimization performed
Questions:
### Q&A
1. xgboost的并行度
  1. 选择特征最佳分裂点时, 进行枚举的时候并行; 树树串行
2. learning rate
  1. 实际为衰减因子, 为了适当减少前面树的影响, 用于控制过拟合(GBDT引入, 和梯度下降算法中的完全不同)
3. xgboost防止过拟合的方法
  1. 目标函数L2 正则
  2. 列抽样,行抽样
  3. shrinkage 学习率

# Ref
1. [Quick Introduction to Boosting Algorithms in Machine Learning](https://www.analyticsvidhya.com/blog/2015/11/quick-introduction-boosting-algorithms-machine-learning/)
2. [Complete Guide to Parameters Tunning in XGBoost with codes in Python](https://www.analyticsvidhya.com/blog/2016/03/complete-guide-parameter-tuning-xgboost-with-codes-python/)
