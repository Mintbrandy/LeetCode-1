---
layout: post
title: LeetCode - Merge Sorted Array
date: 2017-11-9 22:54:56
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 88. Merge Sorted Array

<!--more-->

## 题目

Given two sorted integer arrays *nums1* and *nums2*, merge *nums2* into *nums1* as one sorted array.

**Note:**
You may assume that *nums1* has enough space (size that is greater or equal to *m* + *n*) to hold additional elements from *nums2*. The number of elements initialized in *nums1* and *nums2* are *m* and *n* respectively.

## 解析

合并两个有序数组，将结果保存在第一个数组里，假设数组一的容量足够。

既然是合并，那么合并完之后的元素数量确定 `m + n` ，可以从后往前，依次将元素填充到数组一种。

假设，数组二种的元素全部填充到了数组一种之后，数组一这时已经是想要的最后结果了。

## 代码

``` java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int i = m - 1;
        int j = n - 1;
        int k = m + n - 1;
        while (i >= 0 && j >= 0) {
            nums1[k--] = (nums1[i] > nums2[j] ? nums1[i--] : nums2[j--]);
        }
        while (j >= 0) {
            nums1[k--] = nums2[j--];
        }
    }
}
```