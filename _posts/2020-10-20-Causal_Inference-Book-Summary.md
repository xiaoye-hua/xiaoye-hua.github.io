---
layout: post
title: Casual Inference Book Summary
subtitle: Book Summary of Casual Inference - Why if (by Hernán MA / Robins JM)
date: 2020-10-20
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

This is a book summary for **Casual Inference - Why if** by by Hernán MA and Robins JM. I went through the basic concepts of this book and finished this summary for further reference.
The detailed code for part two can be found [here](https://www.hsph.harvard.edu/miguel-hernan/causal-inference-book/). For next iteration, I will figure out these code. 

# Casual Inference Without Models
## Definition of Causal Inference
1. We compare (usually only mentally) the outcome when an action  is taken
with the outcome when the action is withheld.
2. Individual Causal Effects: 
    1. the treatment has a causal effect on an individual’s outcome if $Y^{a=1} \neq Y^{a=0}$ for the individual ($Y^{a=1}, Y^{a=0}$ are refered as potential outcome or counterfactual outcome).
2. Average causal effects in a population: indicidual causal effects cann't be measured
3. Measure of causal effects:
    1.causal risk difference
    2. risk ratio
    3. odds ratio
4. Association is not causation
5. To analysis causal effects, there are two methods:
    1. Randomied experiments
    2. Observational studies
 
## Randomized Experimens
1. Randomization
    1. Conditional randomization
    2. Marginally randomization
2. Approaches to estimate average causal effects:
    1. Standardiztion
    2. Inverse probability weighting
## Observational Studies
1. Sometimes randomized experiments are not possible, we need to get conclusion from the observation
2. An observational study can be conceptualized as a conditionally randomized experiment under the following three conditions:
    1. Consistency
    2. Exchangeability
    3. Positivity

## Effect Modification
1. Instead of average causal effects in the whole population, many causal questions are about the subset of the population.
2. Effect modifier:
    1. We say that M is the modifier of effect A on Y when the average causal effect of A on Y vaies across the levels of M.
    2. A stratified(分层) analysis is the natural way to identiy effect modifier.
3. In the absence of marginal randomization, achieving the goals requires ajustments to the variable L to ensure conditional exchangeablity of the treated and untreated. Forms of ajustments:
    1. Statification
    2. Matching
        1. Construct a subset of the population in which the varibles L have the same distribution in both treated and untreated.
        2. 
4. Four methods to estimate average causal effect
    1. Both marginal and conditional effects:
        1. IP weighting and standardization
    2. Conditional effects in a subset of population
        1. Statification and matching

## Interaction
Many problems are about the interaction of several treatments. This chapter provides definition of interaction both in **the counterfactual framework** and the **sufficient-component framework**.


1. We refer to interventions on two or more treatments as **joint interventions**.
2. Identification of interaction:
    1. The three key identifying conditions were exchangeability, positivity, and consistency. Because interaction is concerned with the joint effect of two (or more) treatments  and , identifying interaction requires exchangeability, positivity, and consistency for both treatments.
3. suffient-component framework: 
    1. The graphical representation of sufficient-component causes helps visualize a key consequence of effect modification:
4. Two frameworks:
    1. The sufficient-component-cause framework and the counterfactual (potential outcomes) framework address different questions. The counterfactual approach addresses the question “what happens?” Thesufficient-component-cause approach addresses the question “how does it happen?”
        1. The sufficient component cause model considers sets of actions, events, or states of nature which together inevitably bring about the outcome under consideration.
        2.  the potential outcomes framework addresses the question, “What would have occurred if a particular factor were intervened upon and thus set to a different level than it in fact was?”


## Graphical Representation of Causal Effects

1. Causal diagrams:
    1. The modern theory of diagrams for causal inference arose within the disciplines of computer science and artificial intelligence.

## Bias

There are two qualitatively different reasons why causal inferences may be wrong: 

1. systematic bias
    1. selection bias  both of which may arise in observational studies and in randomized experiments
    2. measurement bias–both of which may arise in observational studies and in randomized experiments
    3. unmeasuredconfounding–which is not expected in randomized experiments.
2. random variability.

1. If those factors affect the risk of developing the outcome (e.g., another person’s looking up), then the effects of those factors become entangled with the effect of treatment. We then say that there is confounding, which is just a form of **lack of exchangeability** between the treated and the untreated.
2. Confounding is often viewed as the main shortcoming of observational studies.


Unlike confounding, this type of bias is not due to the presence of common causes of treatment and
outcome, and can arise in both randomized experiments and observational studies. Like confounding, selection
bias is just a form of lack of exchangeability between the treated and the untreated

# Casual Inference With Models
## Why Models?

1. Estimators
    1. Nonparametric estimators
    2. Parametric estimators

## Three Methods to Estimate Average Causal Effects
1. Three methods to estimate the average causal effects (these three methods are often collectively referred to as **g-methods** because they are designed for application to generalized treatment contrasts involving treatments that vary over time.):
    1. how to use IP weighting to estimate this effect from observational data.
    2. how to use standardization to estimate the average causal effect of smoking cessation on body weight gain.
    3. g-estimation.



## Instrumental Variable Estimation

1. The causal inference methods described so far in this book rely on a key untestable assumption: all variables needed to adjust for confounding and selection bias have been identified and correctly measured.It turns out that there exist other methods that can validly estimate causal effects under an alternative set of assumptions that do not require measuring all adjustment factors. Instrumental variable estimation is one of those methods. 
2. 

## Casual Survival Analysis

1. we have been concerned with causal questions about the treatment effects on outcomes occurring at a particular time point.Many causal questions, however, are concerned with treatment effects on the time until the occurrence of an event of interest.
2. The term “survival analysis”, or the equivalent term “failure time analysis”, is applied to any analyses about time to an event
3. 

# Causal Inference from Complex Longitudinal Data

## Time-varying Treatments

1. So far this book has dealt with fixed treatments which do not vary over time. However, many causal questions involve treatments that vary over time.
2. Sequential exchangeability is a key condition to identify the causal effects of time-varying treatments.
3. When treatment-confounder feedback exists, using traditional adjustment methods may introduce bias in the effect estimates.
4. G-methods can be ajusted for time-varying treatments



# Ref

1. [Causal Inference - Why if,douban.com](https://book.douban.com/subject/30454248/)







