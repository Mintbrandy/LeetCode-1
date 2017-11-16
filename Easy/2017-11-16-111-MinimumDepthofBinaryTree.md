---
layout: post
title: LeetCode - Minimum Depth of Binary Tree
date: 2017-11-16 23:02:17
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 111. Minimum Depth of Binary Tree

<!--more-->

## 题目

Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

## 解析

找到与根节点最近的叶子节点，输出最小的深度。

个人认为，如果使用层次遍历，找到根节点就返回所在的层次，可能比递归更快一些，因为这样不用遍历每一个节点。

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
    public int minDepth(TreeNode root) {
        if (root == null) return 0;
        int left = minDepth(root.left);
        int right = minDepth(root.right);
        return (left == 0 || right == 0) ? left + right + 1 : Math.min(left, right) + 1;
    }
}
```