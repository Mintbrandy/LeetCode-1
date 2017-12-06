---
layout: post
title: LeetCode - Sum of Two Integers
date: 2017-12-6 21:42:41
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 371. Sum of Two Integers

<!--more-->

## 题目

Calculate the sum of two integers *a* and *b*, but you are **not allowed** to use the operator `+` and `-`.

**Example:**
Given *a* = 1 and *b* = 2, return 3.

## 解析

不使用加号和减号，计算两个数字的和。

关于数字位运算的一些总结：[A summary: how to use bit manipulation to solve problems easily and efficiently](https://discuss.leetcode.com/topic/50315/a-summary-how-to-use-bit-manipulation-to-solve-problems-easily-and-efficiently)

## 代码

``` java
class Solution {
    public int getSum(int a, int b) {
        if (a == 0) return b;
        if (b == 0) return a;

        while (b != 0) {
            int carry = a & b;
            a = a ^ b;
            b = carry << 1;
        }

        return a;
    }
}
```