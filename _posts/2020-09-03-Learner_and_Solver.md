---
layout: post
title: Learner and Solver
subtitle: The Way to General Intelligence ?
date: 2020-09-03
published: True
mathjax: True
catalog: true
tags:
  - machine learning
  - general intelligence
  - paper reading
---
# TOC
1. Introduction
{:toc}

# Model-free, Model-based and General Intelligence

## Background

1. Learners such as ML or DL infers behaviors or function from data and experience
2. Solvers such as SAT, classicial planning, Bayesian network and POMDPs

## Open Challenges

1. Learner -> big success, but black box
2. Solver -> require models and scalable algorithms

## Main Contributions

1. Review the gaps between model-free and model-based approches
2. Learner and solvers: contract:
    1. Learner: need training, which is slow, then fast; can only learn from experience (intuition mind for system I in psychology)
    2. Solvers: no training, slow to inference;  can solve a problem from scratch provided representation of problems(analytical mind for system II in psychology)
3. Learners and solvers:  challenges:

Model Learning: Learning models from stream of  action and partial observation remains challenging

Learning the relevant variables, learn features that are reusable

Learn finite-size abstract representation -> representation learning for planning

# Reconcoiling Deep Learning with Symbolic Artificial Intelligence: Representing Objects and Relations

## Background

Symbolic artifical intellgence was dominant in 20th century, while a connectionist paradigm become popular now. But they both have advantages and drawbacks. A significant challenge in this field is to effect a reconciliation.

To achieve this goal, the objective of deep learning is to develop structure to discover objects and relations from the data, and learn how to represent them in ways that are useful for the downstream task. This review highlight the recent pregross.

Focus on the question: How the deep learning can acquire compositional representation whose elements are objects and relations

Focus on the folllowing topics:
1. compositionality 
2. learning representations composed of objects and relations

|            Drackbacks           |                              Deep learning                             |                      Symbolic AI                     |
|:-------------------------------:|:----------------------------------------------------------------------:|:----------------------------------------------------:|
|        Data inefficiency        |                                                                        |         symbolic representations can be reuse        |
|      Lack of generalization     |                                                                        | Symbolic representations are high-level and abstract |
|      Lack of interpretation     |                                                                        |          Language-like -> easy to understand         |
| representations are handcrafted | discover features from high-dimensition data without human intervetion |                                                      |

## Objects and Compositionality

In symbol AI, representations  conform a priciple of compositionality to the extent that the denotation of a representations is a function of the denotiions of its parts and the way those part are combined.
1. The representations most of deep learning methods got are distributed, whose element has little or no meaning in isolation. Those factors are entangled.
2. A vallina autoencoder can learn entangled features; while a variational autoencoder can learn disentangled features
3. The learned disentangled feature is benfical to downstream tasks such as reinforcement learning and learning hierarchical concepts (To be researched)

## Relational Representations

How to extract relational representation:
1. Relation network: concate object pairs and pass them into a MLP 
2. Self-attention: compute an additional attention weights for each pair

# Learning First-order Symbolic Representation for Planning from the Structure of States Space

## Background & Challenges

The obstacles for developing flexible AI is the split between data-based learner and model-based solver. This work tried to get a complete first-order representation (i.e. general actions schemas, relations symble, and objects) from non-symbolic input (graph that encode the structure of state space) that encode the structure of the state space 

## Method

The inference problem is cast as a two-level combinatorial search where the outer level looks for the right value of the hyperparameters and the inner level, formulated and solved via SAT, looks for a fifirst-order representation that fifits the hyperparameters and explains the input graphs. 
1. Input: labelled directed graph
2. Ouput: PDDL-like representation

## Experiment & Result

Correct and general first-order models for domains like Gripper, Blocksworld, and Hanoi are shown to be learned from graphs that encode the flflat state-space structure of a single small instance.

# From Statistical Relational to Neuro-Symbolic Artificial Intelligence

## Background

The intergration of learning and reasoning is  one of the key challenge in AI and ML. Neuro-symbolic and statistical relational artificial intelligence both intergrate framework for learning with logic reasoning. This work identified seven paralls across seven dimension between these two fields. This survey limit itself to logic and probabilistic perspective.
1. Neuro-symbolic: incorporate symbolic learning into neural network
2. Statistical relational AI: incroporate logic with probabilistic graphical model

## Comparision (TO DO)

|             Dimension            | StarAI | NeSy |
|:--------------------------------:|:------:|:----:|
|      Directed vs undirected      |        |      |
|       Grounding vs proofing      |        |      |
|  Logic vs probability vs neural  |        |      |
|             Semantic             |        |      |
| Learning paramters  vs structure |        |      |
|       Symbol vs sub-symbol       |        |      |
|           Type of logic          |        |      |

## Open challenges for NeSy

1. Probabilistic reasoning: the application of probabilistic reasoning in neural-symbol approach
2. Structure learning
3. Scaling inference
4. Data efficiency
5. Symbolic representation learning 


# Neural-Symbolic VQA: Disentangling Reasoning from Vision and Language Understanding

## TODO

1. symbolic program executor
2. Details of REINFORCE
    1. how to set the output of question parser 
    2. unsupervised or weakly supervised representation learning

## Problem

[CLEVR: A Diagnostic Dataset for Compositional Language and Elementary Visual Reasoning](https://cs.stanford.edu/people/jcjohns/clevr/)

## Prevous & Current Methods

### Previous

Two seperate approaches:
1. Deep learning
2. symbolic approach

### Current

Current Approach, three components:
1. a scene parser (de-renderer)
2. a question parser (program generator)
3. and a program executor.

<img src='/img/learner_and_solver/current.png' width="600">

## Result & Conclusion & Insight

Three advantages:

1. First, executing programs on a symbolic space is more robust to long program traces; our model can solve complex reasoning tasks better, achieving an accuracy of 99.8% on the CLEVR dataset.

2. Second, the model is more data- and memory-effificient: it performs well after learning on a small number of training data; it can also encode an image into a compact representation, requiring less  storage than existing methods for offlfline question answering. 

3. Third, symbolic program execution offers full transparency to the reasoning process; we are thus able to interpret and diagnose each execution step.

## Limitation & Potential Direction

However, building structured representations for scenes and sentence meanings—the targets of these mappings—in ways that generalize to truly novel situations remains a challenge for many approaches including ours.

Recent progress on unsupervised or weakly supervised representation learning, in both language and vision, offers some promise of generalization. Integrating this work with our neural-symbolic approach to visually grounded language is a promising future 

# CLEVRER: COLLISION EVENTS FOR VIDEO REPRESENTATION AND REASONING

## TODO

1. Dynamics predictor
2. symbolic program executor
3. First limitation 

## Problem

[CLEVRER: CoLlision Events for Video REpresentation and Reasoning](http://clevrer.csail.mit.edu/)

CLEVRER includes four types of question: 
1. descriptive (e.g., ‘what color’)
2. explanatory (‘what’s responsible for’)
3. predictive (‘what will happen next’)
4. counterfactual (‘what if’).

While these state-of-the-art models for visual reasoning thrive on the perceptionbased task (descriptive), they perform poorly on the causal tasks (explanatory, predictive and counterfactual)

## Prevous & Current Methods

### Previous

Three previosu research directions
1. video understanding
2. visual question answering
3. physical and causal reasoning

### Current

Our model Neuro-Symbolic Dynamic Reasoning (NS-DR) combines neural nets for pattern recognition anddynamics prediction, and symbolic logic for causal reasoning.

1. a video frame parser 
2. a neural dynamics predictor 
3. a question parser
4. a program executor
<img src='/img/learner_and_solver/current2.png' width="600">


## Result &Conclusion & Insight
<img src='/img/learner_and_solver/setup.png' width="600">
<img src='/img/learner_and_solver/result.png' width="600">

Contributions
1. First, NS-DR incorporates a dynamics planner into the visual reasoning task
2. Second, symbolic representation provides a powerful common ground for vision, language, dynamics and causality.


## Limitation & Possible Direction

training of the video and question parser relies on extra supervisions such as object masks, attributes, and quesion programs. Even though the amount of data required for training is minimal compared to end-to-end approaches (i.e. thou sands of annotated frames and programs), these data is hard to acquire in real-world applications. This constraint could be relaxed by applying unsupervised/weaklysupervised methods for scene decomposition and concept discovery 
Second, our model performance decreases on tasks that require long-term dynamics prediction such as the counterfactual questions. This suggests that we need a better dynamics model capable of generating more stable and accurate trajectories.



