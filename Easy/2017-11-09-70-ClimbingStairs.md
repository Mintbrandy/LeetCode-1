---
layout: post
title: LeetCode - Climbing Stairs
date: 2017-11-9 21:12:50
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 70. Climbing Stairs

<!--more-->

## 题目

You are climbing a stair case. It takes *n* steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

**Note:** Given *n* will be a positive integer.

**Example 1:**

```
Input: 2
Output:  2
Explanation:  There are two ways to climb to the top.

1. 1 step + 1 step
2. 2 steps

```

**Example 2:**

```
Input: 3
Output:  3
Explanation:  There are three ways to climb to the top.

1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```

## 解析

一共有`n`阶楼梯，一次能走`1`阶或者`2`阶，一共有多少种走法。

使用递归会超时。基本上类似一个斐波那契数列(Fibonacci  sequence)。

`c[n] = c[n-1] + c[n-2]`

## 代码

``` java
class Solution {
    public int climbStairs(int n) {
        if (n == 0)
            return 0;
        int one_step_before = 1;
        int two_step_before = 2;
        int result = 0;
        if (n == 1) {
            return 1;
        }
        if (n == 2) {
            return 2;
        }
        while (n-- > 2) {
            result = one_step_before + two_step_before;
            one_step_before = two_step_before;
            two_step_before = result;
        }
        return result;
    }
}
```