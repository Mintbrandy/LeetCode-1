---
layout: post
title: LeetCode - Intersection of Two Arrays
date: 2017-12-5 23:23:20
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 349. Intersection of Two Arrays

<!--more-->

## 题目

Given two arrays, write a function to compute their intersection.

**Example:**
Given *nums1* = `[1, 2, 2, 1]`, *nums2* = `[2, 2]`, return `[2]`.

**Note:**

- Each element in the result must be unique.
- The result can be in any order.

## 解析

求两个数组的交点。我的理解就是想同的元素，返回数组要去没有重复值。

## 代码

``` java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        Set<Integer> set = new HashSet<>();
        Set<Integer> intersect = new HashSet<>();
        for (int num1 : nums1) {
            set.add(num1);
        }
        for (int num2 : nums2) {
            if (set.contains(num2)) {
                intersect.add(num2);
            }
        }
        int[] result = new int[intersect.size()];
        int i = 0;
        for (int num : intersect) {
            result[i++] = num;
        }
        return result;
    }
}
```