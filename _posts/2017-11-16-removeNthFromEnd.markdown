---
layout:     post
title:      "83. Remove Duplicates from Sorted List"
subtitle:   "Leetcode 83. Remove Duplicates from Sorted List"
date:       2017-11-16 17:24:22 
author:     "Sandra"
catalog: true
tags:
    - Leetcode
---

# 83. Remove Duplicates from Sorted List

## Description:

Given a sorted linked list, delete all duplicates such that each element appear only once.

For example,
Given 1->1->2, return 1->2.
Given 1->1->2->3->3, return 1->2->3.

## Solution
    class Solution(object):
        def deleteDuplicates(self, head):
            """
            :type head: ListNode
            :type n: int
            :rtype: ListNode
            """

            if head == None:
                return []
            l = self.ListNodeToList(head)
            n = []
            for x in l:
                if x not in n:
                    n.append(x)
            return self.ListToListNode(n)

        def ListNodeToList(self,head):
            l=[]
            while head.next:
                l.append(head.val)
                head = head.next
            l.append(head.val)
            return l

        def ListToListNode(self,l):

            if len(l)<1:
                return None

            node = ListNode(l[0])   
            for i in range(1,len(l)):
                self.appendNode(node,ListNode(l[i]))

            return node

        def appendNode(self,node,target):
            while node.next:
                node = node.next
            node.next = target
