---
layout:     post
title:      "集成学习 Ensemble Learning"
subtitle:   "集成学习 Ensemble Learning"
date:       2017-11-30 10:08:07 
author:     "Sandra"
catalog: true
tags:
    - Ensemble Learning
---
#集成学习 Ensemble Learning

集成学习：构建并结合多个学习器来完成学习任务，对于训练集数据，通过训练若干个个体学习器，通过一定的结合策略，就可以最终形成一个强学习器

个体学习器是同质的，应好而不同
好的集成学习 = 准确性 + 多样性

随着基学习器数目增加，集成的错误率指数下降，最终趋向于0
（前提：基学习器的误差相互独立）

集成学习分类：
Boosting：
个体学习器存在强依赖，必须串行生成。训练过程为阶梯状，基模型按次序一一进行训练（实现上可以做到并行），基模型的训练集按照某种策略每次都进行一定的转化。对所有基模型预测的结果进行线性综合产生最终的预测结果。代表：AdaBoost，GBDT, XGBOOST
Bagging：
个体学习器不存在强依赖，可以并行生成。从训练集从进行子抽样组成每个基模型所需要的子训练集，对所有基模型预测的结果进行综合产生最终的预测结果。代表：Random Forest

