---
layout: post
title: LeetCode - Invert Binary Tree
date: 2017-11-29 09:52:56
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 226. Invert Binary Tree

<!--more-->

## 题目

Invert a binary tree.

```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```

```
     4
   /   \
  7     2
 / \   / \
9   6 3   1
```

Trivia:

This problem was inspired by [this original tweet](https://twitter.com/mxcl/status/608682016205344768) by [Max Howell](https://twitter.com/mxcl):

> Google: 90% of our engineers use the software you wrote (Homebrew), but you can’t invert a binary tree on a whiteboard so fuck off.

## 解析

翻转二叉树

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
    public TreeNode invertTree(TreeNode root) {
        if (root == null)
            return null;
        TreeNode temp = root.left;
        root.left = invertTree(root.right);
        root.right = invertTree(temp);
        return root;
    }
}
```