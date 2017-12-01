---
layout:     post
title:      "145. Binary Tree Postorder Traversal"
subtitle:   "145. Binary Tree Postorder Traversal"
date:       2017-12-01 13:07:39
author:     "Sandra"
catalog: true
tags:
    - Leetcode
    - Binary Tree
---

# 145. Binary Tree Postorder Traversal

## Description:

Given a binary tree, return the postorder traversal of its nodes' values.

For example:
Given binary tree [1,null,2,3],
<p>1</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;\</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;/</p>
<p>3</p>

return [3,2,1].

Note: Recursive solution is trivial, could you do it iteratively?

二叉树的后序遍历: 左子树->右子树->根节点

## Solution   
    class Solution(object):
        # 二叉树的后序遍历
        # 左子树->右子树->根节点
        def postorderTraversal(self, root):
            """
            :type root: TreeNode
            :rtype: List[int]
            """
            return self.Recursive(root)
        
        # 使用递归的方式 
        def Iterative(self,root):
            # 声明存放结果的数组
            travelList = []
            self.postOrder(travelList,root)
            return travelList
            
        def postOrder(self,travelList,node):
            if node != None:           
                self.postOrder(travelList,node.left)
                self.postOrder(travelList,node.right)
                travelList.append(node.val)
