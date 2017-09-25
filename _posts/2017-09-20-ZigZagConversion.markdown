---
layout:     post
title:      "6. ZigZag Conversion"
subtitle:   "Leetcode 6. ZigZag Conversion"
date:       2017-09-20 20:37:52
author:     "Sandra"
catalog: true
tags:
    - Leetcode
---

# 6. ZigZag Conversion

## Description:

The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

P   A   H   N
A P L S I I G
Y   I   R

And then read line by line: "PAHNAPLSIIGYIR"
Write the code that will take a string and make this conversion given a number of rows:

string convert(string text, int nRows);

convert("PAYPALISHIRING", 3) should return "PAHNAPLSIIGYIR".

## Solution
    class Solution(object):
        def convert(self, s, numRows):
            """
            :type s: str
            :type numRows: int
            :rtype: str
            """
            
            num = len(s)
            
            # 只有一列或者字符串长度小于2
            if numRows == 1 or num < 2:
                return s
            
            # 两列以上      
            numCols=num/2 + 1  
            pos,matrix = 0,[]
            
            # 初始化矩阵
            for i in range(numRows):
                matrix.append([])            
                for j in range(numCols):                               
                    matrix[i].append([])
                    matrix[i][j] = '-'     
            
            # z型填充矩阵
            for j in range(numCols):
                for i in range(numRows):
                    if (j%(numRows-1)  == 0 or (j+i)%(numRows-1) == 0) and pos<num:
                        matrix[i][j] = s[pos]
                        pos = pos+1
            
            # 拼接变形后的字符串
            result = ''
            for row in matrix:
                print(row)
                for i in row:
                    if i != '-':
                        result = result+i      
            
            return result
                    
