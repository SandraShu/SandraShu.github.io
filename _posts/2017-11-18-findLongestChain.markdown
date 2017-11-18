---
layout:     post
title:      "523. Continuous Subarray Sum"
subtitle:   "Leetcode 523. Continuous Subarray Sum"
date:       2017-11-18 16:49:22 
author:     "Sandra"
catalog: true
tags:
    - Leetcode
    - Dynamic Programming
---

# 523. Continuous Subarray Sum

## Description:

You are given n pairs of numbers. In every pair, the first number is always smaller than the second number.

Now, we define a pair (c, d) can follow another pair (a, b) if and only if b < c. Chain of pairs can be formed in this fashion.

Given a set of pairs, find the length longest chain which can be formed. You needn't use up all the given pairs. You can select pairs in any order.

    Example 1:
    Input: [[1,2], [2,3], [3,4]]
    Output: 2

Explanation: The longest chain is [1,2] -> [3,4]

Note:The number of given pairs will be in the range [1, 1000].

## Solution
    class Solution(object):
        def findLongestChain(self, pairs):
            """
            :type pairs: List[List[int]]
            :rtype: int
            """
            # 数组长度
            n = len(pairs)
            # 长度小于2 返回0
            if n < 2:
                return 0
            # 按照pair[1]排序
            pairs = sorted(pairs,key=lambda x: x[1])
            print(pairs)
            # 遍历
            pos,length = 0,0
            while pos < n:
                # pos
                temp = pos
                # 对pos之后的数据做比较
                for i in range(pos,n):
                    # 判断
                    if pairs[i][0] > pairs[pos][1]:
                        # pos更新位置
                        pos = i
                        # length自增1
                        length += 1
                        # 结束本次循环
                        break
                # 如果此次的遍历 pos的位置没有更新
                # 即没有符合要求的数组出现 
                # 退出
                if pos == temp:
                    break
            return length+1
