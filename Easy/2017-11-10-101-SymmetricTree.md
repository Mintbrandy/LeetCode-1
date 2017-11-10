---
layout: post
title: LeetCode - Symmetric Tree
date: 2017-11-10 23:20:55
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 101. Symmetric Tree

<!--more-->

## 题目

Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

For example, this binary tree `[1,2,2,3,4,4,3]` is symmetric:

```
    1
   / \
  2   2
 / \ / \
3  4 4  3

```

But the following `[1,2,2,null,3,null,3]` is not:

```
    1
   / \
  2   2
   \   \
   3    3

```

**Note:**
Bonus points if you could solve it both recursively and iteratively.

## 解析

判断一颗树是否是对称的。

使用递归：使用一个辅助函数，判断是否对称。

不使用递归：使用队列，进行层次遍历，判断是否符合条件。

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
    public boolean isSymmetric(TreeNode root) {
        return isMirror(root, root);
    }
    
    public boolean isMirror(TreeNode p, TreeNode q) {
        if (p == null && q == null) {
                return true;
            }
            if (p == null || q == null) {
                return false;
            }
            return (p.val == q.val)
                    && (isMirror(p.left, q.right))
                    && (isMirror(p.right, q.left));
    }
}
```
``` java
class Solution {
    public boolean isSymmetric(TreeNode root) {
        Queue<TreeNode> q = new LinkedList<>();
        q.add(root);
        q.add(root);
        while (!q.isEmpty()) {
            TreeNode t1 = q.poll();
            TreeNode t2 = q.poll();
            if (t1 == null && t2 == null) {
                continue;
            }
            if (t1 == null || t2 == null) {
                return false;
            }
            if (t1.val != t2.val) {
                return false;
            }
            q.add(t1.left);
            q.add(t2.right);
            q.add(t1.right);
            q.add(t2.left);
        }
        return true;
    }
}
```

