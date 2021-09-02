---
layout: post
title: Deep Learning Structures Summary
date: 2021-08-30
published: True
mathjax: True
catalog: true
tags:
  - deep learning
  - machine learning
  - summary 2021
---
# TOC
1. Introduction
{:toc}


# CNN

1. What: NN -> unstructure data (computer vision)
2. How: By using diff dim of filters -> 
    1. Advantage:
        1. extract local spatial representation
        2. share of the weights -> increase computation effeciency
    2. components:
        1. CNN
        2. pooling
        3. dense
        4. activation
3. Application:
    1. variations: ResNet, DenseNet
   
1. when striding=1, got the 'same' padding, there should be condition that 
```math
p = \frac{f-1}{2}
```


## AlexNet (2012)

1. key step from shallow NN to deep NN; 
2. Compared to LeNet, 
    1. deeper (8 VS 5)
    2. use ReLU instead of sigmoid as activation function

## VGG (2014)

1. What: the first to use reusable convlution blocks -> allow for effecient design of complex networks
2. How: conv blocks
    1. conv layer
    2. Nonlinearity such as relu
    3. pooling -> for spatial downsampling


## NiN Network in Network (2013)

1. What: change previous strutures: conv + dense,
2. how
    1. previous:
        1. conv + pooling -> extract spatial feature
        2. dense -> postprocess the feature
    2. NiN
        1. conv + 1*1 filter -> more per-pixel nonlinearity
        2. global avg pooling instead of dense ->  avoid overfit , reduce params
        
## GoogLeNet (2015)

1. What: combine the strength of NiN and repeated blocks paradigms, extracting information in parallel
2. How:
    1. extract info in parallel through conv and maxpooling
        1. 1*1 conv  -> reduce channel dimemtions on a per-pixel level
        2. max-pool -> reduce the resolution

## Batch Normanization (2015)

1. What problem:
    1.  accelerate the convergence of the training
2.  How:
    1.  adjust the intermediate output of the NN by utilizing mean and  standard devidation of the minbatch  -> make the output value more stable 
3. Application
    1. Similar to dropout layer,  different computation result for training and predicting process

## ResNet (2015)

1. Background: 
    1. Intuitively, layer of DL are used to extract different level of features, and features will be enrich by the number of stacked layers. However, deeper NN has higher train error, namely model degradation.
2. How: ResNet solved the problem of model degradation by adding a shortcut connection besides the main connection. 
    1. Instead of learning the underline map function, the ResNet model tries to learn the residual function between the underline maping function and the input.
    2. In addition, ResNet partly solved gradient vanishing problem.
        1. shortcut connection -> graidient can be passed passed directly to the previous layers
3. Application

## DenseNet - Densely Connected Network (2017)

1. What:  is to some extent the logical extention of ResNet: every layer is densely connnected to all the previous layers
2. How:
    1. Compare to ResNet
        1. output and input are concatenated together instead of adding
    2. Consis of 
        1. DenseBlock 
        2. TransitionBlock -> control the complexity of the model


# Sequence Model

## Seq2Seq


1. What problem:  initially -> machine tranlation task; RNN-based encoder-decoder structure.
2. How: 
    1. encoder will pass the hidden state of the last step to decoderl; this state serves as a context vector which contains all the information captured in the encoder
    2. Every step of decoder, the context vector, hidden state of previous step, and input of currrent step wil be feeded into the RNN cell

## Attention

1. What problem: Initially used for machine translation task in order to replace the RNN-based Seq2Seq model. It tred to solve that Seq2Seq does not cope with the long distance well (due to the fixed length of context vector)
2. How:  in this way, focus on relevent information
    1. Instead of passing the hidden state of the last timestep to decoder,  attention will pass all hiddens states to the decoder
    2. In every step of decoder,  
        1. with attentiton -> calculate the relationship between current step and the encoder hidden state 
            1. query: hidden state of previous step in decoder
            2. key: hidden states of encoder
            3. value: same as key
        2. the combination of attension info and hidden state of previous step are feeded into the RNN cell together with input vector
3. Example:
    1. English -> Chinese  "the knowledge is the power" -> when translating "knowlege' -> more focus on this word -> improve the model


Different Types of Attentions

1. Scaled dot-product attention
    1. assume that query and key have the same dimension
2. Additive attention
    1.  that query and key have different dimension
3. Multi-head attention
    1. want to capture the info in diff range (e.g long distance or short ) from the distance -> benificial use different represation of query, key, and value 
    2. combine knowleges from different behaviors of the same attention (Dot-Product attention)

## Self-Attention

1. What problem: remove the structure of RNN --> improve computation effecienty
2. How:
    1. In this structure, the query, key and value are the same vector
3. However: no sequence informationa ->  be used together with position encoding

## Transformer

1. What problem: 
    1. By utilizing the advantage of compute effeciency of self-attention,  -> transformer -> widely used in diff domains such NLP, CV, RL.
2. How:
    1. encoder-decoder structure
        1. encoder: embedding and positonal encoding following by the encoder layer
            1. self-attention layer
            2. residual connection and layer normalization
            3. position-wise feedford layer
        2. decoder: embedding and positonal encoding following by the decoder layer
            1. self-attention layer
            2. multi-head attention layer
            2. residual connection and layer normalization
            3. position-wise feedford layer
  
## BERT (Bidirectional Encoder Representation from Transformer)

1. BERT is a pre-trained word embedding model. Compare to previous pre-trained word embedding model, it has two advantage：
    1. context sensitive: encode context information bidirectionally
    2. task-agnostic(不可知): require minimum architechture change for a wide range of NLP tasks
2. How
    1. Pretrained-BERT consisits two task:
        1. Masked language modeling: enable the model to learn context bidirectionally
        2. Next sentence prediction: enable the model to learn the relationship between two sentence
    2. Fine-tune pre-trained word embedding model 
        1. feature-based: such ELMo, embedding will not be fine-tuned, but use taks-specific architecture
        2. task-based: such GPT,  embedding will be fine tuned
        3. for BERT: embdding will be fine-tuned; the new layers will be trained from scratch.
    3. Comparation:
        1. word2vec, Glove: context-nondependent; assign the same vetor to a word regardless of the context of the word
        2. ELMo: context-sensitive, but use task-specific architecture
        3. GPT: context sensitive, but encode from left to right

# Reference
2. [Dive Into Deep Learning](https://d2l.ai/)

