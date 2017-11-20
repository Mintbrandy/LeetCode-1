---
layout: post
title: LeetCode - Single Number
date: 2017-11-20 11:03:48
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 136. Single Number

<!--more-->

## 题目

Given an array of integers, every element appears *twice* except for one. Find that single one.

**Note:**
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

## 解析

给出一个存放数字的数组，每个元素出现两次，除了一个数只出现了一次，找到这个只出现一次的数。

使用异或(`XOR`) 操作。

## 代码

``` java
class Solution {
    public int singleNumber(int[] nums) {
        int result = 0;
        for (int num : nums) {
            result ^= num;
        }
        return result;
    }
}
```