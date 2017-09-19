---
layout:     post
title:      "3. Longest Substring Without Repeating Characters"
subtitle:   "Leetcode 3. Longest Substring Without Repeating Characters"
date:       2017-09-15 11:27:37
author:     "Sandra"
catalog: true
tags:
    - Leetcode
---

# 3. Longest Substring Without Repeating Characters

## Description:

Given a string, find the length of the longest substring without repeating characters.

## Example:

  Given "abcabcbb", the answer is "abc", which the length is 3.

  Given "bbbbb", the answer is "b", with the length of 1.

  Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
  
## Solution
    class Solution(object):
        def lengthOfLongestSubstring(self, s):
            """
            :type s: str
            :rtype: int
            """
            # 滑窗
            i=0
            j=0
            length=0
            target = ''
            num = len(s)
            
            while i<num and j<num:
                if s[j] not in target:               
                    target = target + s[j]
                    j = j+1
                    length = j-i>length and j-i or length
                    #print('y',j,target)
                else:                
                    target = target[1:]
                    i = i+1
                    #print('n',i,target)
                
            return length
