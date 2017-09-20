---
layout:     post
title:      "5. Longest Palindromic Substring"
subtitle:   "Leetcode 5. Longest Palindromic Substring"
date:       2017-09-20 18:24:28
author:     "Sandra"
catalog: true
tags:
    - Leetcode
---

# 5. Longest Palindromic Substring

## Description:

Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

==>最长回文子串

## Example:

  Input: "babad"

  Output: "bab" Note: "aba" is also a valid answer.

  Input: "cbbd"

  Output: "bb"
  
## Solution
    class Solution(object):
        def longestPalindrome(self, s):
            """
            :type s: str
            :rtype: str
            """
            
            # 寻找最长回文子串
            # 中心扩展：把给定的字符串的每一个字母当做中心，向两边扩展，这样来找最长的子回文串
            length,start,num = 0,0,len(s)
            
            # 回文子串长度为奇数
            for i in range(num):
                
                left = i - 1               
                right = i + 1
                
                # print(left,right)
                
                while left>=0 and right<num and s[left]==s[right]:
                    
                    # print(left,right)
                    
                    if right-left+1 > length:
                        
                        length = right-left+1
                        start = left
                        
                    left = left - 1
                    right = right + 1 
            
            # 回文子串长度为偶数
            for i in range(num):
                
                left = i                
                right = i + 1
                
                # print(left,right)
                
                while left>=0 and right<num and s[left]==s[right]:
                    
                    # print(left,right)
                    
                    if right-left+1 > length:
                        
                        length = right-left+1
                        start = left
                        
                    left = left - 1
                    right = right + 1 
                   
            return length>0 and s[start:start+length] or s[0]
                
