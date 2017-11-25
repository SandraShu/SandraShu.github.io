---
layout:     post
title:      "494. Target Sum"
subtitle:   "Leetcode 494. Target Sum"
date:       2017-11-20 16:07:22  
author:     "Sandra"
catalog: true
tags:
    - Leetcode
    - Dynamic Programming
---

# 494. Target Sum

## Description:

You are given a list of non-negative integers, a1, a2, ..., an, and a target, S. Now you have 2 symbols + and -. For each integer, you should choose one from + and - as its new symbol.

Find out how many ways to assign symbols to make sum of integers equal to target S.

Example 1:
    Input: nums is [1, 1, 1, 1, 1], S is 3. 
    Output: 5
    Explanation: 

    -1+1+1+1+1 = 3
    +1-1+1+1+1 = 3
    +1+1-1+1+1 = 3
    +1+1+1-1+1 = 3
    +1+1+1+1-1 = 3

There are 5 ways to assign symbols to make the sum of nums be target 3.
Note:
The length of the given array is positive and will not exceed 20.
The sum of elements in the given array will not exceed 1000.
Your output answer is guaranteed to be fitted in a 32-bit integer.

## Solution
    class Solution(object):
        def findTargetSumWays(self, nums, S):
            """
            :type nums: List[int]
            :type S: int
            :rtype: int
            """
            # 根据数学推导
            # (1) sum(P) - sum(N) = target
            # (2) sum(P) = (target + sumNums)/2
            n = len(nums)
            sumNums = sum(nums)
            sumP = (S + sumNums)/2
            sumN = sumP - S
            
            # 数组长度小于1 or 数组之和小于目标值 or sumP为奇数 返回0
            if n < 1 or sumNums < S:
                return 0
            
            print(sumP,sumN)
            
            # 初始化dp
            dp = [0]*(sumP+1)
            dp[0] = 1
            
            # 遍历
            for x in nums:
                # 判断 数组中是否有和为sumP的子数组
                # ????????????????? 有个Test Case没过
                for i in range(sumP,x-1,-1):
                    dp[i] += dp[i-x]
            
            print(dp)           
            return dp[sumP]