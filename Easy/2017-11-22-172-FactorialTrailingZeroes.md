---
layout: post
title: LeetCode - Factorial Trailing Zeroes
date: 2017-11-22 16:17:38
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 172. Factorial Trailing Zeroes

<!--more-->

## 题目

Given an integer *n*, return the number of trailing zeroes in *n*!.

**Note: **Your solution should be in logarithmic time complexity.

## 解析

给出一个数字 `n`，输出 `n!` 末尾有多少个 `0` 。

Because all trailing 0 is from factors 5 * 2.

But sometimes **one number may have several 5 factors**, for example, 25 have two 5 factors, 125 have three 5 factors. In the n! operation, factors 2 is always ample. So we just count how many 5 factors in all number from 1 to n.

## 代码

``` java
class Solution {
    public int trailingZeroes(int n) {
        int count_5 = 0;
        while (n > 0) {  // 等同于 n >= 5
            n /= 5;
            count_5 += n;
        }
        return count_5;
    }
}
```