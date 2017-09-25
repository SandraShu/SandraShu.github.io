---
layout:     post
title:      "7. Reverse Integer"
subtitle:   "Leetcode 7. Reverse Integer"
date:       2017-09-25 10:34:44 
author:     "Sandra"
catalog: true
tags:
    - Leetcode
---

# 7. Reverse Integer

## Description:

Reverse digits of an integer.

Example1: x = 123, return 321
Example2: x = -123, return -321

Have you thought about this?
Here are some good questions to ask before coding. Bonus points for you if you have already thought through this!

If the integer's last digit is 0, what should the output be? ie, cases such as 10, 100.

Did you notice that the reversed integer might overflow? Assume the input is a 32-bit integer, then the reverse of 1000000003 overflows. How should you handle such cases?

For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

Note:
The input is assumed to be a 32-bit signed integer. Your function should return 0 when the reversed integer overflows.

## Solution
    class Solution(object):
        
        # int32判断，溢出返回0
        def int32(self,x):
            # 2^31
            if x>0x7FFFFFFF:
                return 0
            
            if x<-0x7FFFFFFF:
                return 0
        
            return x
        
        # 字符串反转
        def string_reverse(self,string):  
            return string[::-1]
        
        def reverse(self, x):
            """
            :type x: int
            :rtype: int
            """
            
            if x >= 0:
                return self.int32(int(self.string_reverse(str(x))))
            else:
                return self.int32(-int(self.string_reverse(str(abs(x)))))
                    
