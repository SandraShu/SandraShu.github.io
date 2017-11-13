---
layout:     post
title:      "19. Remove Nth Node From End of List"
subtitle:   "Leetcode 19. Remove Nth Node From End of List"
date:       2017-11-13 17:24:22 
author:     "Sandra"
catalog: true
tags:
    - Leetcode
---

# 19. Remove Nth Node From End of List

## Description:

Given a linked list, remove the nth node from the end of list and return its head.

For example,

   Given linked list: 1->2->3->4->5, and n = 2.

   After removing the second node from the end, the linked list becomes 1->2->3->5.

Note:
Given n will always be valid.
Try to do this in one pass.

## Solution
    class Solution(object):
        def removeNthFromEnd(self, head, n):
            """
            :type head: ListNode
            :type n: int
            :rtype: ListNode
            """
            l = self.ListNodeToList(head)
            del l[len(l)-n]
            a = self.ListToListNode(l)
            return a

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
