---
layout: post
title: Machine Learning Interview Questions 
<!-- subtitle: Deep Learning Explain Series (Part 1) -->
date: 2020-08-01
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
 "when you go through this process, you'll find there are many thing you think you understand but you didn't. You will make connections that you didn't see before and simplied the the information in your head as you try to condense it down and regurgitate it... This step is crucial to retain information and developing more than a surface-understanding of a subject" 

# Question & Answer
### What's the trade-off between bias and variance
1. The goal of machine learning is to reduce the error between the predicted value and the groud truth.
2. The total errors comprises three parts: bias, variance and irreducible error. Irreducible error can not be reduced. Bias is introduced by too simple model, while vairiance is introduced by to complex model
3. If increase the complixity of the model, or add more features, the bias will be reduced. However it might result in overfit, which will increase the variance.
4. We do not expect either high bias or variance. So we need to trade-off bias and variance to find the optimal model.

### Explain how ROC works, explain AUC
1. ROC: it is a curve representing the contract between true positive rate and false positive rate at various threshold。
2. ACU: Area Under The ROC curve. It measures the performance of classification at various threshold
3. Detail meaning for AUC:
    1. 0.5: can not separate two classes
    3. 1: separate it fully 

### Explain precision & recall & F1 score
1. Definition:
    - Precision refers to the number of correctly classified positives over the number of classified positives. 
    - Recall refers to the number of correctly classified positive compared to the number of all positive sample. 
    - F1 score is a weight average of precision and recall. The formula is $\frac{2 \times precision \times recall}{recall + precision}$
2. Example:
    - High precision means the predicted positive are indeed positive
    - High recall represents that the positive are classified correctly.

### Explain Bayes' Theorem. How is it important in a machine learning context?
Ref[6]
- The Bayes's Theorem stats that you can get the posterior probability of an event by combining knowledge from prior probability and information got from your test
- We often found ourself in a situation when we know $P(y \| x)$, however we want $P(x \| y)$. If we also know $P(x)$, we can get the quantity according to Bayes' theorem:  $P(y \| x)=\frac{P(x \| y)P(y)}{P(x)}$

### Why naive Bayes classifier is "naive" ?
- Because it's based on a "naive" assumption. The assumption stats that every feature contributes independently to the target variable


### What is deep learning?
- It is a subset of machine learning. And it's more complex and has more parameters. It can extract hidden feature from large
    amount of data.

### What's more important to you? model accuracy or model performance?
- Of course.  Model performacne is more critical. In my oppoinion, model accuracy is just an acadamic metric. However, model performance depends on the specific details of the problem you're faceing. It might be related to accruracy, precision or recall. It all depends on the problem.
- For example. In order to improve the user experience of a forum, we need to build a toxic commment detection system. Of cource, it's not easy to build a perfect system: there will be cases when normal or toxic comments will be misclassified. When we believe the users will be more upset when their normal comments are deleted by the system compared to be exposed to toxic comments. Model performance is related precision. In this case, we want ensure the detected toxic commments are indeed toxic. On the contract, we might pay more 
attention to recall to detect as more toxic comments as possible.

### How would you handle inbalanced dataset?
1. Definition
    - For example, you have a dataset. 90% of the data are from one class. In this case, if your model classified all the data to the major class, you can still get an accuracy of 90%. However, your model has no predictive power for the minor class.
2. How to handle
    - Collect more data for the minor class
    - Resampling the dataset
    - Try other machine learning algorithms

### How avoid over-fitting 
1. keep model simpler: do not include too many variables
2. cross validation such k-fold cross validation
3. user regularization such as Lasso regression (L1 norm)

### Ridge regression VS Lasso? L1 VS L2 regularization.
1. Ridge and Lasso regression both use regularization term to reduce the variance. Ridge regression use L2 norm of the coefficient vector as the regularization term. While for Lasso regression, it uses L1 norm of the coefficient vector.
2. For Ridge regression, ther L2 penalty term will shrink all of the coeffecients toward zero, but it will not set any of them to exactly zero. However, the L1 penalty will force some coefficients to zero when the $\lambda$ is sufficient large. So Lasso tends to create a sparse model, a model with only a subset of the variable.
3. Take regression problem as an example. The following is the objective functions for linear regression, ridge regression and Lasso regression
    - $\sum_{i=1}^{n}(y_i- \beta_0+\sum_{j=1}^{p}\beta_j x_{ij})$
    - $\sum_{i=1}^{n}(y_i- \beta_0+\sum_{j=1}^{p}\beta_j x_{ij}) + \lambda \sum_{j=1}^{p}\beta^{2}$
    - $\sum_{i=1}^{n}(y_i- \beta_0+\sum_{j=1}^{p}\beta_j x_{ij}) + \lambda \sum_{j=1}^{p}\|\beta\|$

### What's the difference between Type-I and Type-II error
1. Type-I error means false positive, which means you are claiming something has happened when it hasn't; Type-II error is false negative, which means you claim something does not happend while it actually has happended.
2. Take an example:
    - Type-I error: a man has pregnant
    - Type-II error: you tell a pregnant woman she doesn't carry a baby.

### What's the difference between probability and likelihood?
Ref[2][3]
1. Probability is the percentage of the success
2. Likelihood: the probability of the data given the model parameters. It's conditionaly prabobility.

### Expalin maximum likelihood
- When working with probabilistic model with unknown paramters, the paramters that make the data with the highest prabobility is the most likely ones.

### What's the difference between generative and discriminative model?
Ref[4][5]
1. Definition:
    - Generative model such naive Bayes, Bayes network, tries to model the distribution of input X give the label y. However, the discriminative model such as logistic regression, NN or SVM, will try to learn mapping directly from input X to label y.
2. Examples:
    - Take an example: if we want to train a classification model to distinguish cats and dogs
        - For generative model, it will first create a model of cat, then learn a model of dog. When classifying a new animal, it will compare it with the dog model, then the cat model to whether the new animal looks more like the dogs or cats in our training data.
        - For discriminative model, it will learn the decision boundary between the dog and cat. It will check which sides the new animals falls, and make prediction accordingly.



# Ref
1. An Introduction to Statistical Learning with Application in R
2. Dive into Deep Learning
3. [What's the Difference between Probability and Likelihood? - Quora](https://qr.ae/pNsJld)
4. [CS299 Course Note - Generative Learning Algorithms](http://cs229.stanford.edu/notes/cs229-notes2.pdf)
5. [Machine Learning: Generative and Discriminative Model](https://cedar.buffalo.edu/~srihari/CSE574/Discriminative-Generative.pdf)
6. Deep Learning by Ian Goodfellow





# Other Questions

1. Approches to remove curse of dimensionality
    1. two approchs
        1. feature reduction
            1. remove corrected predictors ()
            2. forward, beackword stepwise feature selection
            3. recursive feature selection 
        2. feature extraction
            1. PCA


16. p value ?  
    1. It's use in hypothesis testing. meaning the probability of observing the thing we observed 
    assuming the null hypothesis is true
    2. if p value is bigger than a threshold, then we can't reject null hypothesis. Otherwise, 
    reject null hypothesis
19. confusion matrix
             prediction:  positive  negative     
      observations:   
      positive             TP        FN
      negative             FP       TN

22. How to handle imbalanced(skewed) datasets
    1. collect more data;
    2. re-sampling
        1. over-sampling: copy paste over-represented class
        2. under-sampling: sampling data
    3. different algorithms: Tree algorithms works better with unbalanced data. the split rules force unbalance to be addressed
23. when use classification over regression
    1. classification creates discrete output; regression creates continuous values
    2. if want to predict categorical value, use classification
24. what's the idea behind ensemble learning (name a example ensemble learning are used)
    1. use for reduce overfitting, making model more robust; 
    2. idea: create a strong learner by combining the result of several weak learner
    2. methods including : bagging, boosting, stacking
        1. bagging : random forest 
        2. boosting : gbdt(gradient boost decision tree)
        3. stacking: average the results of several models (stack lightGBN and NN result together)
