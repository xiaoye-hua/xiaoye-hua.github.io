---
layout: post
title: Customer-life-time-value(CLTV) Prediction Review
date: 2020-06-20
published: True
mathjax: True
catalog: true
tags:
  - machine learning application
  - paper reading
---
# TOC
1. 背景
{:toc}

# Potential Applications

Recently, I've done a project to predict the customer life-time value of hundred millions of users in a e-commence company. This is a summary for that project and also a small review for CLTV prediction.


In e-commence companies, customer Life-time value is an important property. Based on the life-time value, companies can allocate resources to high-value customer in order to get a high Return of Investment (ROI). In addition, based on the predicted customer life-time value, companies can launch market compaign for different user segmentation. Overal, the customer life-time value can be benifit to the following services:

1. User acquisition
2. User service
3. In-app purchase
4. Pricing and promotion

# Challenge & Potential Solution

1. Problem definition
    1. revenue related definition
        1. profit: influenced by margins
        2. gross profit
        3. frequency of order
    2. engagement related definition 
        1. frequency of login
        2. community contribution (comments contribution ...)
2. LTV values vary across different users
    1. Plenty of 0
        1. Two stage model
            1. classification: whether will LTV be zero
            2. regression: the specific number of LTV
        2. Clustering  ->  develop models for every cluster
            1. For different group, measuring LTV in different dimension might also be possible. e.g zero-order users can be measured with engagement-related LTV
    2. extreme values exist
        1. Predict percentiles instead of real value -> map percentiles to real value later
        2. Transformation (log)
        3. Remove the value
3. Trigger events influence user's behaviors
    1. seasonality 
    2. coupon to attract new users
    3. bad experience purchase
    4. customer service interaction such as call, refund
4. Scaling problem because of the magnitude of the user base.
    1. update partially
    2. Simple model for majority, complex model for those who go through trigger events


# Features

## Feature Dimension


1. User demographic features: gender, age, occupation..
2. User behavior feature 
    1. review, purchase, order, products in the carts
    2. interaction with the seller (in the chanel of chat, video streaming...)
3. Platform intervention
    1. coupons intervention
    2. average margins of our product 
4. Features related to previous CLTV 
    1. LTV in previous week, month, half-year, year
    2. standard deviation of monthly LTV in previous year...
 
## Potential Important Features

1. Purchase value in the past quarter
2. Purchase value in the past year
3. Lifetime purchase value
4. Number of days since most recent purchase

# Paper Reading

## An Engagement-Based Customer Lifetime Value System for E-commerce

**背景和假设**

发表时间：2016年

Groupon 是一个与美团类似的团购网站，目前其系统每天预测用户价值。预测尺度为
1. short - 一个季度
2. medium -- 三个季度
3. long  -- 一年

本文假设，对于不同生命周期的用户，其价值的影响因素不同，最后在分群特征重要度处有体现。预测值为 purchase value:

We use a proxy measure for customer value that we will call “purchase value” that is based on purchasing behavior, focusing on this behavior instead of profifit because the latter is subject to margins that can influctuate and that are not related to user intent.

商品实际的profit和当时的商品利润相关，跟用户的意图关系不大。GTV才跟用户意图最相关？

**特征**

一共采用40多个特征，主要有以下方面

1. engagement: 与邮件的交互，和在平台上的搜索
2. user experience：
    1. 用户居住地附近的商品数等
    2. 用户服务： 用户给的差评，用户退货次数，到货时间等
3. user behavior： 历史价值，订单，优惠券等
4. Other, such as demographiic：年龄，性别，居住城市的特征，注册时特征等。

**方法**

1. 用户分群 根据用户购买历史，分为5个用户群 (对于不同生命周期的用户，其价值的影响因素不同的假设)
    1. Unactivated
    2. One-time buyer
    3. Sporadic buyer
    4. Power users
2. 分群LTV预测（分类+回归问题）(对于不同分群，进行LTV预测，所用模型为Random Forest，分为两个阶段)
    1. 预测用户是否会下单
    2. 在1的基础上，预测会下单用户的LTV值
3. Seasonality & decay model这两个模型基于实际的业务和工程考虑，起到补丁的作用：
    1. 模型是基以季度为周期进行训练的，同时不同季度间用户购买行为有变化，所有根据历史数据，增加季度间的修正参数
    2. 由于用户数的庞大，每天更新全量用户成本较高。同时观察到用户在"triggr event"之后的LTV变化有一定规律性，于是采用以下策略：
        1. 通过模型更新有“trigger event”的用户
        2. 对于没有“trigger event” 的用户，直接使用原有值乘以经验得到的衰减参数。

**效果**

整体效果评估参数：

1. Pearson and Spearman correlation coefficient
2. RMSE, bias in the averages,
3. a comparison of actual versus predicted distributions.
4. top 10%  revenue VS bottom 90%
5. Predicted inclinded revenue VS real case
整体效果如下：
<img src='/img/ltv_paper/ltv_paper1.png' width="600">
几个结论：
    1. 时间长度越长，预测越准
    
## Customer Lifetime Value Prediction Using Embeddings
**背景和假设**

ASOS-总部位于英国，全球性时尚服饰和美妆产品线上零售商。

发表时间：2017年

本文中介绍了两部分：
1. churn model. 采用两级预测，先用RF预测概率，然后再用LR修正概率
2. CLTV model. 主要采用Random Forest模型。

流失用户和LTV预测的范围如下：

We define a customer as churned if they have not placed an order in the past year. We define CLTV as the sales, net of returns, of a customer over a one year period.

两个模型中都强调了 model calibration 的作用

同时文章提出生成user embedding, churn 模型效果有提升，CLTV模型上还没尝试，然而资源成本太高，未上线。

**特征**

主要从以下四个维度抽取132个特征

1. customer demographics,
2. purchase history 
3. returns history
4. web and app session logs. (最多的特征)

最后得出的特征重要度如下：
<img src='/img/ltv_paper/feature1.png' width="600">

web/app session log 的重要度仅次于purchases history

**方法**

预测步骤：

由于LTV数量级分布差异比较大, 故做了两级预测:
1. RF模型预测用户的LTV大小在总体分数的分位(范围0-1)
2. RF模型将预测的分位映射到LTV的具体数值上

**效果**

CLTV model: Spearman rank-order correlation coefficient 
1. 0.56 (for all customers) 
2. 0.46 (excluding customers with a CLTV of 0)

<img src='/img/ltv_paper/result1.png' width="600">


## Customer Lifetime Value Prediction in Non-Contractual Freemium Settings
**背景和假设**

本文主要关注于游戏应用的LTV预测，主要方法为：

用MLP, decision tree, LR 预测，MLP效果较好

用SMOTE 对高价值用户（比较少）进行过采样， 效果较好

**特征**
<img src='/img/ltv_paper/feature2.png' width="600">

**Ref**

1. [SMOTE知乎解释](https://zhuanlan.zhihu.com/p/44055312)


## A DEEP PROBABILISTIC MODEL FOR CUSTOMER LIFETIME VALUE PREDICTION

**背景 & 贡献**
场景：新用户的LTV预测

主要贡献
1. 摒弃两级模型的预测结构，用一个模型解决问题，
2. 用新的loss function解决以下问题  
    1. 0的数值较多
    2. 数据分布的倾斜 （20/80 rule）
3. 整体模型值得借鉴
    1. model calibration 值得借鉴

    
# Ref

1. Jamal, Zainab, and Alex Zhang. "2008 DMEF customer lifetime value modeling (Task 2)." Journal of Interactive Marketing 23.3 (2009): 279-283.
2. Vanderveld, Ali, et al. "An engagement-based customer lifetime value system for e-commerce." Proceedings of the 22nd ACM SIGKDD international conference on knowledge discovery and data mining. 2016.
3. Learning, Deep, and Big Data. "Customer Lifetime Value Prediction Using Embeddings."
4. Kooti, Farshad, et al. "iPhone's Digital Marketplace: Characterizing the Big Spenders." Proceedings of the tenth ACM international conference on web search and data mining. 2017.
5. Sifa, Rafet, et al. "Customer lifetime value prediction in non-contractual freemium settings: Chasing high-value users using deep neural networks and SMOTE." Proceedings of the 51st Hawaii International Conference on System Sciences. 2018.
6. Wang, Xiaojing, Tianqi Liu, and Jingang Miao. "A deep probabilistic model for customer lifetime value prediction." arXiv preprint arXiv:1912.07753 (2019).
7. Jasek, Pavel, et al. "Predictive performance of customer lifetime value models in e-commerce and the use of non-financial data." Prague Economic Papers 28.6 (2019): 648-669.
8. Malthouse, Edward C. "The results from the lifetime value and customer equity modeling competition." (2009): 272-275.







