---
layout: post
title: LeetCode - Balanced Binary Tree
date: 2017-11-16 22:30:05
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 110. Balanced Binary Tree

<!--more-->

## 题目

Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of *every* node never differ by more than 1.

## 解析

判断是否是平衡二叉树。

平衡二叉树的左右子树都是平衡二叉树，而且左右子树的高度相差不超过1。

使用深度优先搜索，算法复杂度为 `O(n)`

## 代码

``` java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public boolean isBalanced(TreeNode root) {
        return dfsHeight(root) != -1;
    }
    
    public int dfsHeight(TreeNode root) {
        if (root == null) return 0;

        int leftHeight = dfsHeight(root.left);
        if (leftHeight == -1) return -1;

        int rightHeight = dfsHeight(root.right);
        if (rightHeight == -1) return -1;

        if (Math.abs(leftHeight - rightHeight) > 1) return -1;

        return Math.max(leftHeight, rightHeight) + 1;

    }
}
```