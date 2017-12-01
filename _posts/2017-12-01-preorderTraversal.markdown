---
layout:     post
title:      "144. Binary Tree Preorder Traversal"
subtitle:   "144. Binary Tree Preorder Traversal"
date:       2017-12-01 11:07:39
author:     "Sandra"
catalog: true
tags:
    - Leetcode
    - Binary Tree
---

# 144. Binary Tree Preorder Traversal

## Description:

Given a binary tree, return the preorder traversal of its nodes' values.

For example:
Given binary tree [1,null,2,3],
<p>1</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;\</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;/</p>
<p>3</p>

return [1,2,3].

Note: Recursive solution is trivial, could you do it iteratively?

二叉树的前序遍历: 根节点->左子树->右子树

## Solution

!!!敲重点!!!
- 迭代: 更新变量的旧值, 循环结构，例如for，while循环
- 递归: 在函数内部调用自身, 选择结构，例如if else 调用自己，并在合适时机退出
    
    # 分别使用递归与迭代的方式实现
    class Solution(object):
        # 二叉树的前序遍历
        # 根节点->左子树->右子树
        def preorderTraversal(self, root):
            """
            :type root: TreeNode
            :rtype: List[int]
            """
            return self.Iterative(root)
        
        # 使用迭代的方式    
        def Recursive(self,root):
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
                while curNode != None:
                    # 添加该节点的值
                    travelList.append(curNode.val)
                    # 丢进堆栈
                    travelStack.append(curNode)
                    # 当前节点为节点的左孩子
                    curNode = curNode.left
                # 堆栈POP
                curNode = travelStack.pop()            
                # 当前节点为节点的右孩子
                curNode = curNode.right
            return travelList 
        
        # 使用递归的方式 
        def Iterative(self,root):
            # 声明存放结果的数组
            travelList = []
            self.preOrder(travelList,root)
            return travelList
            
        def preOrder(self,travelList,node):
            if node != None:
                travelList.append(node.val)
                self.preOrder(travelList,node.left)
                self.preOrder(travelList,node.right)
