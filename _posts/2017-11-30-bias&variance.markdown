---
layout:     post
title:      "Bias & Variance"
subtitle:   "Bias & Variance"
date:       2017-11-30 10:32:07 
author:     "Sandra"
catalog: true
tags:
    - Machine Learning
---

# 偏差与方差的理解

泛化误差 = 偏差(Bias) + 方差(Variance) + 噪声

+ 偏差：度量了学习算法的期望预测与真实结果的偏离程度

+ 方差：度量了同样大小的数据集的变动所导致的学习性能的变化，即刻画了数据扰动所造成的影响,模型的稳定性

+ 噪声：表达了在当前学习任务上任何学习算法所能达到的期望泛化误差的下界，刻画了学习问题本身的难度

<img src="/img/in-post/bias&variance-1.png">

<strong>泛化性能是由学习算法的能力，数据的充分性，以及学习任务本身的难度所共同决定的</strong>

<img src="/img/in-post/bias&variance-2.png">

充分拟合数据
 -> 模型复杂度增加
 -> 偏差降低
 -> 易过拟合

数据扰动影响小 
 -> 模型复杂度降低
 -> 方差降低
 -> 易欠拟合



