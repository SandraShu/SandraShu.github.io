---
layout:     post
title:      "4. Median of Two Sorted Arrays"
subtitle:   "Leetcode 4. Median of Two Sorted Arrays"
date:       2017-09-19 10:18:13
author:     "Sandra"
catalog: true
tags:
    - Leetcode
---

# 4. Median of Two Sorted Arrays

## Description:

There are two sorted arrays nums1 and nums2 of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

## Example:
  nums1 = [1, 3]
  nums2 = [2]

  => The median is 2.0

  nums1 = [1, 2]
  nums2 = [3, 4]

  => The median is (2 + 3)/2 = 2.5
  
## Solution
    class Solution(object):
        def findMedianSortedArrays(self, nums1, nums2):
            """
            :type nums1: List[int]
            :type nums2: List[int]
            :rtype: float
            """
            
            # Find the median of the two sorted arrays. 
            # The overall run time complexity should be O(log (m+n)).
            
            '''
            # 1.粗暴连接再排序       
            n = nums1 + nums2
            n.sort()
            length = len(n)
            if length%2 == 1:
                return n[length/2]
            else:
                return (float(n[length/2 - 1]) + float(n[length/2]))/2
            '''
            
            # 2.两数组分开遍历
            A, B = nums1, nums2
            m, n = len(A), len(B)
            # 寻找长的数组B，中位数一定在其中
            if m > n:
                A, B, m, n = B, A, n, m
            if n == 0:
                raise ValueError
            
            # 嗷我绕不过来了 =, =
            imin, imax, half_len = 0, m, (m + n + 1) / 2
            while imin <= imax:
                i = (imin + imax) / 2
                j = half_len - i
                if i < m and B[j-1] > A[i]:
                    # i is too small, must increase it
                    imin = i + 1
                elif i > 0 and A[i-1] > B[j]:
                    # i is too big, must decrease it
                    imax = i - 1
                else:
                    # i is perfect   
                    if i == 0: max_of_left = B[j-1]
                    elif j == 0: max_of_left = A[i-1]
                    else: max_of_left = max(A[i-1], B[j-1])
        
                    if (m + n) % 2 == 1:
                        return max_of_left
        
                    if i == m: min_of_right = B[j]
                    elif j == n: min_of_right = A[i]
                    else: min_of_right = min(A[i], B[j])
        
                    return (max_of_left + min_of_right) / 2.0
            
