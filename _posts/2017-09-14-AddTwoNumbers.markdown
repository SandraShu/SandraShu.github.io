---
layout:     post
title:      "2. Add Two Numbers"
subtitle:   "Leetcode 2. Add Two Numbers"
date:       2017-09-14 14:35:44
author:     "Sandra"
catalog: true
tags:
    - Leetcode
---

# 2. Add Two Numbers

## Description:

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

## Example:

  Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)

  Output: 7 -> 0 -> 8
  
## Solution
    class Solution(object):
            
        def node_to_list(self,l):      
            result = []   
            while l is not None:  
                result.append(l.val)
                l = l.next 
            return result
                
        def addTwoNumbers(self, l1, l2):
            
            """
            :type l1: ListNode
            :type l2: ListNode
            :rtype: ListNode
            """
            
            l1 = self.node_to_list(l1)
            l2 = self.node_to_list(l2)
            
            a = 0
            for i in range(len(l1)):
                a = a + l1[i] * 10 ** i
                           
            b = 0
            for i in range(len(l2)):
                b = b + l2[i] * 10 ** i

            c = str(a + b)
            
            head = ListNode(int(c[0]))
            for i in range(1,len(c)):
                n = ListNode(int(c[i]))
                n.next = head
                head = n
            
            print(self.node_to_list(head))
            return head
