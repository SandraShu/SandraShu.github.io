---
layout:     post
title:      "94. Binary Tree Inorder Traversal"
subtitle:   "Leetcode 94. Binary Tree Inorder Traversal"
date:       2017-12-01 10:07:39
author:     "Sandra"
catalog: true
tags:
    - Leetcode
    - Binary Tree
---

# 94. Binary Tree Inorder Traversal

## Description:

Given a binary tree, return the inorder traversal of its nodes' values.

For example:
Given binary tree [1,null,2,3],
   1
    \
     2
    /
   3
return [1,3,2].

## Solution
# Definition for a binary tree node.
    class TreeNode(object):
        def __init__(self, x):
            self.val = x
            self.left = None
            self.right = None

    class Solution(object):
        # 二叉树的中序遍历
        def inorderTraversal(self, root):
            """
            :type root: TreeNode
            :rtype: List[int]
            """
            # 声明堆栈
            travelStack = []
            # 声明存放结果的数组
            travelList = []
            # 设置当前节点为根节点
            curNode = root
            # 当前节点不是空节点 or 堆栈里有节点
            # 目的: 遍历二叉树
            while curNode != None or len(travelStack) > 0:
                # 当前节点不是空节点
                # 目的: 遍历找到最底下的左孩子
                while curNode != None:
                    # 丢进堆栈
                    travelStack.append(curNode)
                    # 当前节点为节点的左孩子
                    curNode = curNode.left
                # 堆栈POP
                curNode = travelStack.pop()
                # 添加该节点的值
                travelList.append(curNode.val)
                # 当前节点为节点的右孩子
                curNode = curNode.right
            return travelList  
