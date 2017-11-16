---
layout:     post
title:      "64. Minimum Path Sum"
subtitle:   "Leetcode 64. Minimum Path Sum"
date:       2017-11-16 21:59:22 
author:     "Sandra"
catalog: true
tags:
    - Leetcode
---

# 64. Minimum Path Sum

## Description:

Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right which minimizes the sum of all numbers along its path.

Note: You can only move either down or right at any point in time.

Example 1:

    [[1,3,1],
     [1,5,1],
     [4,2,1]]

Given the above grid map, return 7. Because the path 1→3→1→1→1 minimizes the sum.

## Solution Idea

Mark 动态规划

## Solution
    class Solution(object):
        def minPathSum1(self, grid):
            """
            :type grid: List[List[int]]
            :rtype: int
            """
            m = len(grid)
            n = len(grid[0])

            if m < 1 or n < 1:
                return 0

            minLen = [grid[0][0]]
            #首先每一个路径的上一个路径都是来自于其上方和左方
            #现将最上面的路径进行求和，最左边的路径进行求和
            for i in range(1,n):
                minLen.append(minLen[i-1] + grid[0][i])
            for i in range(1,m):
                for j in range(n):
                    if j == 0:
                        minLen[j] += grid[i][0]
                    else:
                        minLen[j] = min(minLen[j-1],minLen[j])+grid[i][j]
            return minLen[n-1]

        def minPathSum(self,grid):

            m = len(grid)
            n = len(grid[0])
            print(m,n)

            if m < 1 or n < 1:
                return 0

            minLen = [[0]*n for i in range(m)]
            minLen[0][0] = grid[0][0]

            # 计算第一行的值
            for i in range(1,n):
                minLen[0][i] = minLen[0][i-1] + grid[0][i]

            # 计算第一列的值
            for i in range(1,m):
                minLen[i][0] = minLen[i-1][0] + grid[i][0]

            # 计算其他的值
            # 只能从左边或者上面来 
            for i in range(1,m):
                for j in range(1,n):
                    minLen[i][j] = min(minLen[i-1][j],minLen[i][j-1]) + grid[i][j]
            
            return minLen[m-1][n-1]
