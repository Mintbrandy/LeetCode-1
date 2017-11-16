---
layout: post
title: LeetCode - Convert Sorted Array to Binary Search Tree
date: 2017-11-16 21:53:34
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 108. Convert Sorted Array to Binary Search Tree

<!--more-->

## 题目

Given an array where elements are sorted in ascending order, convert it to a height balanced BST.

## 解析

根据已经排好序的数组构造平衡二叉查找树。

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
    public TreeNode sortedArrayToBST(int[] nums) {
        return sortedArrayToBSTHelp(nums, 0, nums.length - 1);
    }
    
    public TreeNode sortedArrayToBSTHelp(int[] nums, int first, int last) {
        if (first > last) {
            return null;
        }
        if (first == last) {
            TreeNode newNode = new TreeNode(nums[first]);
            return newNode;
        }
        int mid = (first + last) >>> 1;
        TreeNode t = new TreeNode(nums[mid]);
        t.left = sortedArrayToBSTHelp(nums, first, mid - 1);
        t.right = sortedArrayToBSTHelp(nums, mid + 1, last);
        return t;
    }
}
```