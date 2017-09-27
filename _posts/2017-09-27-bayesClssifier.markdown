---
layout:     post
title:      "Bayes Classifier"
subtitle:   "bayes Classifier"
date:       2017-09-27 10:34:44 
author:     "Sandra"
catalog: true
tags:
    - Classifier
---

# Bayes Classifier

## Description:

设以下模式类别具有正态概率密度函数：
         ω1：{(0 0)T, (2 0)T, (2 2)T, (0 2)T}
         ω2：{(4 4)T, (6 4)T, (6 6)T, (4 6)T}
    （1）设P(ω1)= P(ω2)=1/2，求这两类模式之间的贝叶斯分类器


## Solution
    def bayesClassifier(x):
        
        # 向量初始化 Example1
        #w1 = np.transpose(np.matrix([[0,0,0],[1,0,0],[1,0,1],[1,1,0]]))
        #w2 = np.transpose(np.matrix([[0,0,1],[0,1,1],[0,1,0],[1,1,1]]))
        
        # 向量初始化 Example
        w1 = np.transpose(np.matrix([[0,0],[2,0],[2,2],[0,2]]))
        w2 = np.transpose(np.matrix([[4,4],[6,4],[6,6],[4,6]]))
        
        # 均值向量
        m1 = np.matrix(np.mean(w1,1))
        m2 = np.matrix(np.mean(w2,1))
        
        # 协方差矩阵
        c1 = np.matrix(np.cov(w1))
        c2 = np.matrix(np.cov(w2))
        
        # 协方差矩阵的逆
        ci1 = np.matrix(c1.I)
        ci2 = np.matrix(c2.I)
        
        # 套入公式
        a = np.dot((m1-m2).T,ci1)
        b = -(np.dot(np.dot(m1.T,ci1),m1))/2 + (np.dot(np.dot(m2.T,ci2),m2))/2
        
        # 判断类别
        if np.dot(a,x)+b > 0:
            print('w1')
        else:
            print('w2')