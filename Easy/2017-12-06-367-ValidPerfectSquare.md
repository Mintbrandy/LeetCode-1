---
layout: post
title: LeetCode - Valid Perfect Square
date: 2017-12-6 21:24:06
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 367. Valid Perfect Square

<!--more-->

## 题目

Given a positive integer *num*, write a function which returns True if *num* is a perfect square else False.

**Note:** **Do not** use any built-in library function such as `sqrt`.

**Example 1:**

```
Input: 16
Returns: True

```

**Example 2:**

```
Input: 14
Returns: False
```

## 解析

判断一个数是否是一个数的平方。

`A square number is 1+3+5+7+...`

## 代码

``` java
class Solution {
    public boolean isPerfectSquare(int num) {
        int i = 1;
        while (num > 0) {
            num -= i;
            i += 2;
        }
        return num == 0;
    }
}
```