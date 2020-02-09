---
layout: post
title: Deep Learning Course Note (Part 3)
subtitle:  Convolutional Neutral Network (Part A)
date: 2018-02-10
published: True
mathjax: True
catalog: true
tags:
  - deep learning
  - machine learning
  - 学习笔记-course note
  - 公开课-MOOC
---

这是本系列课程的第四门课程,这门课程主要介绍卷积神经网络,其先介绍了卷积神经网络基础知识,后重点介绍了几个已有的成熟的神经网络模型,之后课程将注意力关注于物体检测,人脸识别和风格迁移等实际应用层面.

1. 卷积神经网络基础
{:toc}

这个课程被分为三篇博客介绍, 此篇博客主要介绍卷积神经网络基础和图像分类算法.

将解决的问题
--
本节课中要解决的计算机视觉问题有三个：
+ 图像分类(image classificator)
+ 物体检测(Object detection)
+ 神经风格迁移(Neutral style transfer)

卷积神经网络基础
--

**边缘检测问题**

如下图，可以用特定的滤波器(filter)来实现图像中边缘检测问题，进而引出**卷积**

<img src='/img/deep_learning_course/edge_detection.png' width='800' height='600'>

**Padding & Stridding**

无padding的标准卷积的缺点:
+ 输出网格变小
+ 损失一些信息,特别是边缘信息

Valid and same convolution:
+ valid:  (n, n)\*(f, f) $\longrightarrow$ (n-f+1, n-f+1)
+ same:  Input size = output size

最终维度为:

(n, n) image, padding p, (f, f) filter, $\longrightarrow$ ($\frac{n+2p-f}{s} + 1$, $\frac{n+2p-f}{s} + 1$)

**卷积神经网络中的层**

1. Convolution (CoNN)
2. Pooling (POOL)
3. Fully Connected (FC)

**Pooling Layer**

分为max pooling 和 average pooling. 无参数.-
步幅为m, 则输出为n/m

**Pooling layer 的作用???**

**卷积(convolution)和互相关(cross-correlation)**

神经网络中的卷积在**数字图像处理**中实际为互相关,而实际的卷积运算会对核(Kernel)进行翻转.由于**惯例**,神经网络中称为卷积

<img src='/img/deep_learning_course/cross_correlation.png' width='800' height='600'>

**为什么选用卷积**

课程中解释了两个优点:
+ 参数共享: 每个特征会被多次利用, 同时参数数量相对fullly connected减少很多
+ 稀疏连接: 每个输出只赖于部分输入参数, 减少过拟合.

图片识别CNN实例研究和实用建议
--

本节研究的实例主要有:

+ 经典实例
    + LeNet-5
    + AlexNet
    + VGG
+ Redidual Network (ResNet)
+ Inception neutral network

**经典实例**

LeNet 最初用于识别数字.它的基本结构为Input layer -> CNN layer -> Pooling layer -> CNN layer -> Pooling layer -> FC layer -> FC layer -> Output layer. 大约有6万个参数.

<img src='/img/deep_learning_course/LeNet.png' width = '800'>

模型提出时池化层采用average pool, 各激活层采用Sigmoid和tanh函数.

AlexNet 结构比LeNet复杂.大约有6千万个参数.

<img src='/img/deep_learning_course/AlexNet.png' width='800'>

VGG结构使用了固定的CNN层和Pooling层, 包含一亿三千万的参数:

CONV = (3, 3) filter, s=1, same

MAX-POOL = (2, 2), s=2

<img src='/img/deep_learning_course/VGG.png' width='800'>


**ResNet(residual network 残差神经网络)**


下面展示了一个**普通神经网络**中的残差模块:
<img src='/img/deep_learning_course/residual_block.png' width=800>

如上图, 相当于有一个捷径, 从$a^{[l]}$直接连接到$a^{[l+2]}$之前, 公式$$a^{[l+1]} = g(z^{[l+2]} + a^{[l]})$$ 取代了公式  $a^{[l+2]}=g(z^{[l+2]})$

在图片识别中的残差神经网络如下图, 由上面的公式易知, 需要保证$a^{[l]}$和$z^{[l+2]}$的维度相同, 于是在CNN大多使用**same convolution**. 一般结构为 Input layer -> CNN -> CNN -> POOL.....-> output layer

<img src='/img/deep_learning_course/plain_vs_resnet.png' width=800>

同时介绍了使用残差神经网络的优点:随着神经网络越来越深, 原因为梯度消失. 其效率受到限制, 运用resnet可以提高效果, 如下图
<img src='/img/deep_learning_course/res.png.png' width=800>

Inception Network
--

Inception network 的初始想法是将多种网络层同时用上, 如下图
<img src='/img/deep_learning_course/inception_motivation.png' width=700>

同时在Inception network中使用了**(1, 1)的卷积层**,用来压缩输入参数的第三个维度, 进而大大减少参数, 减少计算量. 如下为其作用展示:
<img src='/img/deep_learning_course/1*1_convolution.png', width=800>

下图为一个**Inception 模块**, 多个模块可构成一个大的inception网络
<img src='/img/deep_learning_course/inception_module.png' width=600>
Inception Network
<img src='/img/deep_learning_course/inception_network.png' width=800>

**图片识别实用建议**

1. 使用已有的开源的神经网络结构来开始你的项目
2. 迁移学习, 使用别人已经训练好的权重然后根据需要进行调整, 如下图:
<img src='/img/deep_learning_course/transfer_learning.jpg' width=800>
3. 数据扩充(对于计算机视觉问题):
    + 计算机视觉会碰到数据不足的问题, 可用以下方法进行数据扩充: 镜像, 随机切割, 颜色调整

课程中也提到了对于参加竞赛的一些建议:
1. 集成(ensembling): 训练多个模型, 平均计算结果
2. 测试时对照片进行多种切割, 如下:
<img src='/img/deep_learning_course/bechmark.png' width=800>

**计算机视觉现状**
下图展示了数据量大小和手动调参工作的关系:
<img src='/img/deep_learning_course/state_of_art.jpg' width=800>
