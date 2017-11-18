---
layout:     post
title:      "523. Continuous Subarray Sum"
subtitle:   "Leetcode 523. Continuous Subarray Sum"
date:       2017-11-17 17:24:22 
author:     "Sandra"
catalog: true
tags:
    - Leetcode
    - Dynamic Programming
---

# 523. Continuous Subarray Sum

## Description:

Given a list of non-negative numbers and a target integer k, write a function to check if the array has a continuous subarray of size at least 2 that sums up to the multiple of k, that is, sums up to n*k where n is also an integer.

Example 1:
    Input: [23, 2, 4, 6, 7],  k=6
    Output: True
    Explanation: Because [2, 4] is a continuous subarray of size 2 and sums up to 6.
Example 2:
    Input: [23, 2, 6, 4, 7],  k=6
    Output: True
    Explanation: Because [23, 2, 6, 4, 7] is an continuous subarray of size 5 and sums up to 42.

Note:
The length of the array won't exceed 10,000.
You may assume the sum of all the numbers is in the range of a signed 32-bit integer.

## Solution
    class Solution(object):
        def checkSubarraySum(self, nums, k):
            """
            :type head: ListNode
            :type n: int
            :rtype: ListNode
            """
            # 数组长度
            n = len(nums)
            # 如果和为零 或 数组长度小于2 返回 False
            if (k == 0 and sum(nums) != 0) or n < 2:
                return False
            # 如果和为零 并且数组元素都为0  返回 True
            if k == 0 and sum(nums) == 0:
                return True
            # 遍历
            for i in range(n-1):
                # init dp
                dp = [0]*(n-i)
                dp[0] = nums[i]
                # 遍历下一位
                for j in range(i,n):
                    # 求和
                    dp[j-i] = dp[j-i-1] + nums[j]
                    # 判断子数组之和是否为k的倍数
                    if dp[j-i] % k == 0 and j != i:
                        #print(i,j,dp[j-i])
                        return True
            return False
