---
layout: post
title: LeetCode - Binary Tree Paths
date: 2017-12-1 10:46:10
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 257. Binary Tree Paths

<!--more-->

## 题目

Given a binary tree, return all root-to-leaf paths.

For example, given the following binary tree:

```
   1
 /   \
2     3
 \
  5

```

All root-to-leaf paths are:

```
["1->2->5", "1->3"]
```

## 解析

输出二叉树从根节点到叶子节点的所有路径

方法一：使用一个函数进行递归查找，通过传参保存每次遍历的节点。

方法二：使用 `foreach` 循环，这里需要思考递归的消耗问题。

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
    public List<String> binaryTreePaths(TreeNode root) {
        List<String> paths = new ArrayList<>();
        if (root != null) {
            searchBT(root, "", paths);
        }
        return paths;
    }
    private void searchBT(TreeNode root, String path, List<String> paths) {
        if (root.left == null && root.right == null) {
            paths.add(path + root.val);
        }
        if (root.left != null) {
            searchBT(root.left, path + root.val + "->", paths);
        }
        if (root.right != null) {
            searchBT(root.right, path + root.val + "->", paths);
        }
    }
}
```
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
    public List<String> binaryTreePaths(TreeNode root) {
        List<String> paths = new ArrayList<>();
        if (root == null) return paths;
        if (root.left == null && root.right == null) {
            paths.add(root.val + "");
        }
        for (String path : binaryTreePaths(root.left)) {
            paths.add(root.val + "->" + path);
        }
        for (String path : binaryTreePaths(root.right)) {
            paths.add(root.val + "->" + path);
        }
        return paths;
    }
}
```

