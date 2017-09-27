---
layout:     post
title:      "感知机(perceptron)训练算法"
subtitle:   "感知机(perceptron)训练算法"
date:       2017-09-27 19:34:44 
author:     "Sandra"
catalog: true
tags:
    - Classifier
---

# 感知机(perceptron)训练算法

## Description:

<img src="/img/in-post/perceptron-1.png">
<img src="/img/in-post/perceptron-2.jpg">

## Solution
	def iterator(w1,w2,w):
	    count = w1.shape[0] + w2.shape[0]
	    for x in w1:
	        if np.dot(w,x.T) <= 0:
	            w = w + x
	            count = count - 1
	    for x in w2:
	        if np.dot(w,x.T) <= 0:
	            w = w + x
	            count = count - 1
	    
	    # 判断是否继续迭代
	    if count != w1.shape[0] + w2.shape[0]:
	        return [False,w]
	    return [True,w]
	    

	def perceptron(w1_,w2_):
	    
	    # 将属于w2的训练样本乘以-1，并写成增广向量的形式
	    w1 = np.column_stack((w1_,np.ones((w1_.shape[0],1))))
	    w2 = np.column_stack((w2_,np.ones((w2_.shape[0],1))))  
	    w2 = np.multiply(w2,np.matrix(np.zeros((w2.shape))) - np.matrix(np.ones((w2.shape))))
	    
	    # 迭代
	    w = np.zeros((1,w1.shape[1]))
	    flag = False
	    while flag == False:
	        result = iterator(w1,w2,w)
	        flag = result[0]
	        w = result[1]
	    print('w',w)