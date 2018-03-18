---
layout: post
title: LeetCode - Arranging Coins
date: 2018-3-16 20:06:08
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 441. Arranging Coins

<!--more-->

## 题目

You have a total of *n* coins that you want to form in a staircase shape, where every *k*-th row must have exactly *k* coins.

Given *n*, find the total number of **full** staircase rows that can be formed.

*n* is a non-negative integer and fits within the range of a 32-bit signed integer.

**Example 1:**

```
n = 5

The coins can form the following rows:
¤
¤ ¤
¤ ¤

Because the 3rd row is incomplete, we return 2.
```

**Example 2:**

```
n = 8

The coins can form the following rows:
¤
¤ ¤
¤ ¤ ¤
¤ ¤

Because the 4th row is incomplete, we return 3.
```

## 解析

纯数学问题，也可以模拟摆放过程

## 代码

``` java
class Solution {
    public int arrangeCoins(int n) {
        return (int) ((-1 + Math.sqrt(1 + 8 * (long) n)) / 2);
    }
}
```