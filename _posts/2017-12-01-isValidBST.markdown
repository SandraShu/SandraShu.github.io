---
layout:     post
title:      "98. Validate Binary Search Tree"
subtitle:   "98. Validate Binary Search Tree"
date:       2017-12-01 16:07:39
author:     "Sandra"
catalog: true
tags:
    - Leetcode
    - Binary Tree
---

# 98. Validate Binary Search Tree

## Description:

Given a binary tree, determine if it is a valid binary search tree (BST).

Assume a BST is defined as follows:

The left subtree of a node contains only nodes with keys less than the node's key.
The right subtree of a node contains only nodes with keys greater than the node's key.
Both the left and right subtrees must also be binary search trees.

Example 1:
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;/&nbsp;&nbsp;&nbsp;&nbsp;\</p>
<p>1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3</p>
<p>Binary tree [2,1,3], return true.</p>

Example 2:
<p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1</p>
<p>&nbsp;&nbsp;&nbsp;&nbsp;/&nbsp;&nbsp;&nbsp;&nbsp;\</p>
<p>2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3</p>
<p>Binary tree [1,2,3], return false.</p>


## Solution
    import sys
    # Definition for a binary tree node.
    class TreeNode(object):
        def __init__(self, x):
            self.val = x
            self.left = None
            self.right = None

    class Solution(object):
        def isValidBST(self, root):
            """
            :type root: TreeNode
            :rtype: List[int]
            """
            if root == None:
                return True
            return self.isValidBSTFunction(root,-sys.maxsize,sys.maxsize)

        def isValidBSTFunction(self,node,minVal,maxVal):
            
            if node == None:           
                return True
            
            if node.val <= minVal or node.val >= maxVal:
                return False
            
            # 左子树 (minVal, node.val)
            # 右子树 (node.val, maxVal)
            return self.isValidBSTFunction(node.left, minVal, node.val) and self.isValidBSTFunction(node.right, node.val, maxVal)
