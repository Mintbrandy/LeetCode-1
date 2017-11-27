---
layout: post
title: LeetCode - Contains Duplicate
date: 2017-11-27 22:50:48
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 217. Contains Duplicate

<!--more-->

## 题目

Given an array of integers, find if the array contains any duplicates. Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

## 解析

判断数组中是否有重复

## 代码

``` java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> numSet = new HashSet<>(nums.length);
        for (int num : nums) {
            if (numSet.contains(num))
                return true;
            numSet.add(num);
        }
        return false;
    }
}
```