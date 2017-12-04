---
layout: post
title: LeetCode - Range Sum Query - Immutable
date: 2017-12-4 22:35:35
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 303. Range Sum Query - Immutable

<!--more-->

## 题目

Given an integer array *nums*, find the sum of the elements between indices *i* and *j* (*i* ≤ *j*), inclusive.

**Example:**

```
Given nums = [-2, 0, 3, -5, 2, -1]

sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3

```

**Note:**

1. You may assume that the array does not change.
2. There are many calls to *sumRange* function.

## 解析

当需要多次输出时，需要使用“缓存”处理

`sumRange(i, j) = sum[j + 1] - sum[i]`

## 代码

``` java
class NumArray {
    private int[] sum;

    public NumArray(int[] nums) {
        sum = new int[nums.length + 1];
        for (int i = 0; i < nums.length; i++) {
            sum[i + 1] = sum[i] + nums[i];
        }
    }

    public int sumRange(int i, int j) {
        return sum[j + 1] - sum[i];
    }
}

/**
 * Your NumArray object will be instantiated and called as such:
 * NumArray obj = new NumArray(nums);
 * int param_1 = obj.sumRange(i,j);
 */
```