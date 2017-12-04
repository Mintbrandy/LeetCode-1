---
layout: post
title: LeetCode - Power of Three
date: 2017-12-4 22:55:43
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 326. Power of Three

<!--more-->

## 题目

Given an integer, write a function to determine if it is a power of three.

**Follow up:**
Could you do it without using any loop / recursion?

## 解析

判断一个数是否是`3`的幂数

看答案去吧，把所有都想到了

## 代码

``` java
class Solution {
    public boolean isPowerOfThree(int n) {
        return n > 0 && 1162261467 % n == 0;
    }
}
```