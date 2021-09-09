---
layout: post
title: Probability & Statistics Summary 
<!-- subtitle:  Reinforcement Learning Basic - Concepts and Taxonomy -->
date: 2021-09-03
published: False
mathjax: True
catalog: true
tags:
  - machine learning
  - Probability & Statistics
  - summary 2021
---

# TOC
1. Introduction
{:toc}


# Estimation
## Statistic Inference

General class of statistic inference

1. Prediction
2. Experiment design
3. Statistical decision making based on the experiments


Refer to book (in WPS) Probabilities and Statistics 7.1

## Prior and Posterior Distribution

1. Prior distribution of the parameters: the distribution of parameters before obverving any data; this distribution tells us the uncertainty to the paramters before observing the data
2. posterior distribution of the prameters: the conditional distribution of the paramters given the observed data
3. The likelihood measures how much the data will change our uncertainty.


## Maximum A Posterior (MAE, Bayes Estimators) & Maximum Likelihood Estimator (MLE)

MLE VS MAE:

1. Both used to estimate the parameters of models to explain the observed datasets;  
    1. Maximum Likelihood Estimator (MLE) is frequentist method, 
    2. while Maximum A Posterior (MAP) is a Bayesian method
2. Difference:
    1. MLE: Maximize the likelihood function P(X/theta) 
        1. We choose parameters so as to maximize the likelihood function (how likely the outcome would happen given the current data and our model)
    2. MAP:
        1. Maximize the posterior function P(theta/X) —> P(X/theta)*P(theta); there is a prior assumption about the distribution of theta
        2. If P(theta) is uniform distribution -> MAP -> MLE: MLE is a special form of MAP
        
 
Ref
1. [MLE vs MAP: the connection between Maximum Likelihood and Maximum A Posteriori Estimation - Agustinus Kristiadi's Blog}](https://wiseodd.github.io/techblog/2017/01/01/mle-vs-map/)
2. [A Gentle Introduction to Maximum a Posteriori (MAP) for Machine Learning](https://machinelearningmastery.com/maximum-a-posteriori-estimation/)
3. Chapter 5 Machine Learning Basic - Deep Learning by Ian Goodfellow




# Hypothsis Test

## Confidence Interval

1. When: It's used when we want to konw how variable the sample result is; CI is used to measure the uncertainty of the sample result.
2. What:
    1. CI is a range of numbers
    2. tt actually measure the prob that the ture value will fall into a interval. That prob is called confidence level
3. Change 
    1. wider CI => more uncertainty about the sample result.
4. For example: 
    1. 90% confidence means if we calculate CI several time based on different sample,  there is a probability 90% that this interval will contain the true value
4. For example
    1. height of US citizen 


Keep in mind:

1. The true value is deterministic, the confidence interval is the variable.
2. Given the confidence interval, the probability the confidence interval contains the true value will be ether be 0 or 1.



## Power

1. When: it's used in binary hypothesis test
2. What: 
    1. (Tech) the conditional probability that we reject the null hypothesis given the alternative hypothesis is true
    2. (Layman) the likelihood a test can detect the different when the difference present
3. For example
    1. the bigger the power, the more confident we are to our experiment result
4. Application: 
    1. it's usually used in experiment design
        1. to decide the sample number



## P-value
1. When: P-value is widely used in hypothsis test. 
2. What:
    1. It's the conditional probability 
    2. we get the result as extreme as the observed result given the null hypothesis is true
3. Change:
    1. small p-value -> more confidence about the alternative hypothesis
    2. In practice, we use 0.05
    3. p-value < 0.05 => reject the null hypothesis
4. For example
    1. height of US citizen

## Type I error

1. When: False positive rate. It's widely used to caterize errors in A/B testing
2. What: 
    1. The error that we reject the null hypothesis when the null hypothesis is true
3. For example
    1. In A/B test, we believe there is a significant change, but there is not


## Type II error

1. When: False negtive rate. It's widely used to caterize errors in A/B testing
2. What: 
    1. The error that we can't reject the null hypothesis when the alternative hypothesis is true
3. For example
    1. In A/B test, we believe there is no significant change, but there is.


## Skewed Observation
The A/B tests looks at the mean of the observation. The Central Limit Theoriem implied that, under general condition, the mean will be a normal distribution and the distribution will become more normal if more more data are added


How would you run an A/B test if the observations are extremely right-skewed?

1. llower the variability by modifying the metric
    1. e.g. revenue in e-commence is right-skewed
    2. Instead of revenue, consider two metrics
        1. convertion rate
        2. the conditional revenue if converted
2. cap values
    1. e.g purchase order in e-commence
        1. some stores instead of individual customer will purchase many order. Just remove these cases
3. percentile metrics
4. log transforms
        
        
## A/B testing

### Concept
1. Describe A/B testing. 
    1. A/B test -> 
        1. Goal: check influence of treatment
        2. How: 
            1. Two group
            2. Compare result -> check if there is influence 


### Pitfalls
What are some common pitfalls?
    2. Common pitfalls ([ref1](https://cxl.com/blog/12-ab-split-testing-mistakes-i-see-businesses-make-all-the-time/)):
        1. Except treatment, there others different factors between two groups
        2. Not enough time and traffic to get significant result (bigger A/A test)
        
        
 ### Interface 
 
 #### Social Network
 
 #### Two-sided Market
        
        
## Applied Regression Analysis


### Multi-variable Regression

1. Beta coeffecient of muti-variable regression
    1. compare the contributions of each independent variables to the dependent variables. The higher the absolute value, the stronger the effect
    2. For example, a beta of .9 has a strong effect than that of .8
2. How to estimate
    1. Least square methods
    2. Maximum likelihood methods

### Logistice Regression

1. How to interprete the confidence interval for logistic regression?
    1. confident interval for beta coeffecient
    2. e.g. 90% CT means that 90% of the time the real value will fall into the CT


[What is a Standard Beta Coeffecient?](https://www.statisticshowto.com/standardized-beta-coefficient/)


# Ref

1. [Couse Note of Applied Regression Analysis from PennState Unversity](https://online.stat.psu.edu/stat462/node/83/)
2. [Confidence Interval, P-value, Power, Type I and Type II Error - YouTube Explain](https://www.youtube.com/watch?v=Allap_hrjyo)
3. [Handle Skewed Data In A/B Testing](https://qr.ae/pGZYXZ)