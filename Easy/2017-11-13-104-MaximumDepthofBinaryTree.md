---
layout: post
title: LeetCode - Maximum Depth of Binary Tree
date: 2017-11-13 22:25:43
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 104. Maximum Depth of Binary Tree

<!--more-->

## 题目

Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

## 解析

求二叉树的最大深度。

使用递归，这里需要注意，我使用 `?:`运算符时，会超时，使用 `Math.max(int a, int b)` 顺利通过。

那么使用 `Math`的 `max(int, int)` 函数要比 `?:` 快？

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
    public int maxDepth(TreeNode root) {
        if (root == null) {
            return 0;
        }
        return 1 + Math.max(maxDepth(root.left), maxDepth(root.right));
    }
}
```