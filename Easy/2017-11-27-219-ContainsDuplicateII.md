---
layout: post
title: LeetCode - Contains Duplicate II
date: 2017-11-27 23:02:07
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 219. Contains Duplicate II

<!--more-->

## 题目

Given an array of integers and an integer *k*, find out whether there are two distinct indices *i* and *j* in the array such that **nums[i] = nums[j]** and the **absolute** difference between *i* and *j* is at most *k*.

## 解析

判断数组中是否存在相同的数，并且它们之间的距离最大为 `k` 。采用一种滑动窗口的思想，最多保存`k`个数值。

## 代码

``` java
class Solution {
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        Set<Integer> numSet = new HashSet<>(k + 1);
        for (int i = 0; i < nums.length; i++) {
            if (i > k) {
                numSet.remove(nums[i - k - 1]);
            }
            if (!numSet.add(nums[i])) {
                return true;
            }
        }
        return false;
    }
}
```