---
layout: post
title: LeetCode - Lowest Common Ancestor of a Binary Search Tree
date: 2017-11-30 13:18:20
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 235. Lowest Common Ancestor of a Binary Search Tree

<!--more-->

## 题目

Given a binary search tree (BST), find the lowest common ancestor (LCA) of two given nodes in the BST.

According to the [definition of LCA on Wikipedia](https://en.wikipedia.org/wiki/Lowest_common_ancestor): “The lowest common ancestor is defined between two nodes v and w as the lowest node in T that has both v and w as descendants (where we allow **a node to be a descendant of itself**).”

```
        _______6______
       /              \
    ___2__          ___8__
   /      \        /      \
   0      _4       7       9
         /  \
         3   5

```

For example, the lowest common ancestor (LCA) of nodes `2` and `8` is `6`. Another example is LCA of nodes `2` and `4` is `2`, since a node can be a descendant of itself according to the LCA definition.

## 解析

找到一个二叉查找树中两个节点的最小祖先节点。

> 判断两个数 `a，b` 分布在 `c` 的两侧，可以使用 `(c - a) * (c - b)` 与 `0` 比较判断。

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
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        while ((root.val - p.val) * (root.val - q.val) > 0) {
            root = root.val > p.val ? root.left : root.right;
        }
        return root;
    }
}
```