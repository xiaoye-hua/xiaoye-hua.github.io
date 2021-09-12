---
layout: post
title: Traditional Machine Learning Summary
date: 2021-09-01
published: False
mathjax: True
catalog: true
tags:
  - machine learning
  - summary 2021
---
# TOC
1. Introduction
{:toc}

# Basic of Machine Learning

# Discriminative Model VS Generative Model

1. Machine learning model can be categorized into two types: Discriminative and generative model. 
    1. Discriminative model draws the decision boundary in the dataset space. And it focuses more to predict the label of the new data
    2. Generative model tries to model how the the data are placed through the dataset space. It focuses more explaining how the data are generated
1. Discriminative:
    1. Steps
        1. Assume the function form of P(Y/X)
        2. Based on training data, estimate the parameters of P(Y/X)
    2. Examples
        1. linear regression
        2. NN
        3. Decision tree
        4. ...
2. Generative：
    1. Steps
        1. Assume the function form of P(Y), P(X/Y)
        2. Based on training data, estimate the parameters of P(Y) and P(X/Y)
        3. Based on Bayes Theorem, get the posterior distribution of P(Y/X)
    2. Examples:
        1. Naive Bayes
        2. Bayesian network
        3. ...
4. Comparision
    1. Discriminative model performs better in the senarios of missing data and small dataset. But if the assumption of conditional independence violates, it performs poor

Ref:

1. [Deep Understanding of Discriminative and Generative Model](https://www.analyticsvidhya.com/blog/2021/07/deep-understanding-of-discriminative-and-generative-models-in-machine-learning/)

## Bias-Variance Trade-off

1. It's a problem encountered when training the ML model.
    1.  Bias: Error reduced by underfiting 
    2.  Variance: Error reduced by overfitting
    3.  We need to trade off these two values in order to get a optimal model
2. Detail explain: 
    1. Training error = bias + variance + irreduciable error => we can only control bias and variance while training
    2. High bias means that the model is too simple that it extract all useful information from the training data
    3. Hig variance means that the model is too complex that it extract noise information from the training data

Ref:

1. [Interview Questions: What's the Bias-variance Trade-off ?](https://machinelearningspecialist.com/machine-learning-interview-questions-q1-whats-the-trade-off-between-bias-and-variance/)

# Linear Regression

## Assumption of linear regression

1. (Relationship)Linear Relationship: The relationship between the independent and dependent variables should be linear. 
    1. This can be tested using scatter plots.
2. (Features) No Multicollinearity: There is little or no multicollinearity in the data. Multicollinearity happens when the independent variables are highly correlated with each other. 
3. (Features) Multivariate Normal: All the variables together should be multivariate normal. For all the variables to be multivariate normal each variable separately has to be univariate normal means a bell shaped curve.And any subset of variables should also be multivariate normal. This can be tested by plotting a histogram.
    1. Multicollinearity can be tested with correlation matrix.
    2. This is derived from Central Limit Theorem
4. (Error) the error tems are unrelated (No Autocorrelation): There is little or no autocorrelation in the data. Autocorrelation means a single column data values are related to each other. In other words f(x+1)is dependent on value of f(x). 
    1. Autocorrelation can be tested with scatter plots.
    2. In this case, the standard error will be underestimated (For example, we copy the training data,  traning number is doubled -> SE is narrowed down by a factor of square root of 2)
5. Homoscedasticity: Homoscedasticity is there. This means “same variance” .In other words residuals are equal across regression line. Homoscedasticity can also be tested using scatter plot.
    1. Standard error, confidence interval are based on that


## Standard Error, Cofidence Interval & Hypothesis Tesing


Standard Error can be calcualted based on the following equation (Ref 1):

```math
\frac{\sigma^2}{n} (\sigma: mean; n: observation number)
```

Based on stardard error, confidence interval for beta can be calculated as follow: 

```math
[\beta -SE(\beta), \beta +SE(\beta)]
```

95% confidence interval means that: with 95% of prabability, the interval will contain the true value of the paramters

## Model Evaluation

### R2

R2 indicates the fraction of variability that is explained by X in this model
```math
R^2 = \frac{TotalSumofSquare-ResidualSumofSquare}{TotalSumofSquare}
```
```math
TotalSumOfSquare = \sum(y-\tilde{y})^2 
```
```math
ResidulSumOfSquare = \sum(y-y^{\prime})^2 
```

### Adjusted R2

1. Adjusted R2 indicates the fraction of variablitity that explained only by the indepent variable that actually affect the target value. It is always no bigger than R2.
2. R2 always decreases as more features are added; however, for adjusted R2, more useful features -> increase; more useless feature -> descrease
3. Formular is as follows:
```math
adjusted R^2 = 1 - \frac{RSS*(n-d-1)}{n-1}
```
n: number of training data; d: number of features used


# Classification

## Logistic Regression

## Linear Discriminant Analysis

1. LDA is a linear model for classification. And it can also an supervised approach for dimentionality reduction. 
2. The intuition behind it is that the algorithm trys to find a linear comnination of the input variables that achieve the maximium seperation from samples between different class and the minimum seperation for samples within the class.
    1. There are many ways for frame and solve LDA, e.g the Bayes theorem(ref1) and Fisher's linear discriminant(ref3) funciton
    2. Assumptions of LDA
        1. The input features follows normal distribution
        2. All the input features share the same variance
3. Compare to Logistice regression
    1. LDA can be applied to mult-label classification
    2. LDA performs better for well-separated data
    3. LDA performs better when sample number is small and the features follows normal distribution
4. The optimization methods is actually a MAP method (Maximum A posterior)


Ref:

1. ISLR
2. [LDA for Dimensionality Reduction in Python](https://machinelearningmastery.com/linear-discriminant-analysis-for-dimensionality-reduction-in-python/)
3. [Dimensionality Reduction via LDA](https://iksinc.online/2018/11/12/dimensionality-reduction-via-linear-discriminant-analysis/)
# Extended Linear Model

1. By replacing least square fitting method, extened model solve the disadvantage of linear model:
    1.  if n is larger than p, -> overfit 
    2.  Some variable are irrelevant -> less model interpetability
2. Three methods
    1. Subset selection -> subsample feature mannully
    2. Regularization -> subsample feature automatically
    3. Dimension reduction -> 


## Subset Methods

## Regularization: Lasso & Ridge Regression


### Ridge

1. Ridge regression can be used to reduce overfitting.
2. How 
    1. lambda * L2 norm of coeffecient are added to the loss function; 
    2. the coeffecients of features will be force towards 0, but it includes all the features in the model
3. Pro & Cons
    1.  It can apply coeffecient shrinkage; 
    2.  work well on the highly correlated featuers
        1.  beacuse include all feaures and coefficients will be distributed among the features based on the correlation.
    3.  Since all features included -> less computational effeciency
 

### Lasso

1. Lasso perform coeffecient shrinkage and feature selection. It can reduce overfiting and provide sparse solution
2. How
    1.  lambda * L1 norm of coeffecient are added to the loss function -> the coeffecients of features will be force towards 0, can be zero
    2.  Some features will be ruled out
3. Compare
    1.  computation effeciently
    2.  perform bad on correlated features:
        1.  it will select one of the highest correlated one and left the coeffecients to zero


## TODO Dimension Reduction Methods

# Finished SVM

# Finished Bayes Classifier

# Model Evalutation

## Precision & Recall & F1 Score (Ref3)

1. Precision: 
    1. indicates an example labeled as positive is indeed positive
    2. divide the total number of correct labled positive by the total number of sample that are labeled as positive
2. Recall
    1. Indicates the class is correctly labeled
    2. divide the total number of correct labled positive by the total number of samples that are positive
3. Precison & recall
    1. High recall, low precision:This means that most of the positive examples are correctly recognized (low FN) but there are a lot of false positives. 
    2. Low recall, high precision:This shows that we miss a lot of positive examples (high FN) but those we predict as positive are indeed positive (low FP)
4. F1 score:
    1. Combination of precision and recall
    2. 2*precision*recall / (precision + recall)

## AUC

1. Metric for binary classification problem. It measures the performance of binary classifier with different threshold.
2. How:
    1. Area under the ROC curve. 
    2. By change the threshold of the classifier, we can plot the FPR as x axis, TPR as y axis.
    3. We want the TPR is much higher than FPR for every threshold, as result we want to maximize the area under this curve 
3. Change:
    1. auc approaches 1 -> better
    2. 0.5 -> can no classify correctly


# Model Explaining

## Shaply value

1. What: come from game theory -> evaluate the value's impact to the predicted vlaue; 
2. How :
    1. Shapley values calculate the importance of a feature by comparing what a model predicts with and without the feature. However, since the order in which a model sees features can affect its predictions, this is done in every possible order, so that the features are fairly compared

Ref

1. [Shap Value - Kaggle learning](https://www.kaggle.com/dansbecker/shap-values)
2. [Shap Python package](https://github.com/slundberg/shap)
3. 合作博弈论：Shapley value - 孙佳伟的文章 - 知乎
https://zhuanlan.zhihu.com/p/82462362
4. TODO: https://geophy.com/insights/whats-the-shap-how-crime-influences-property-value/

# Unsupervised Learning

## Finished K-means

## Hierarchical Clustering

1. Hierarchical clustering is one of unsupervised learning methods for clustering. 
    1. It's used a hierarchical decomposition of the data based on the group similarity. 
    2. Compared to the K-means, we don't need to set the number of clusters before training
2. It will build a tree structure from data similarity. Based on the way to construct the way, there are two ways:
    1. addictive HC: create tree bottom-up
    2. divisive HC: creat tree top-down
    3. Addictive HC is usually used in the industry.
3. Details:
    1. Fist layer, group data based on their similarity
    2. Use the similar method to construct the above layers
    
    
Ref

1. [Hierarchical Clustering and Its Application](https://towardsdatascience.com/hierarchical-clustering-and-its-applications-41c1ad4441a6)
2. [Hierarchical Clustering in Python](https://www.analyticsvidhya.com/blog/2019/05/beginners-guide-hierarchical-clustering/)

## TODO Evaluation

# Ref

1. Introduction to Statistic Learning and Application in R
2. [A Complete Tutorial on Lasso and Ridge Regression in Python](https://www.analyticsvidhya.com/blog/2016/01/ridge-lasso-regression-python-complete-tutorial/#h2_10)
3. [Confusion Matrix Explained](https://www.geeksforgeeks.org/confusion-matrix-machine-learning/)