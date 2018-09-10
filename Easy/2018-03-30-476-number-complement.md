---
layout: post
title: LeetCode - Number Complement
date: 2018-3-30 22:31:30
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 476. Number Complement

<!--more-->

## 题目

Given a positive integer, output its complement number. The complement strategy is to flip the bits of its binary representation.

**Note:**

1. The given integer is guaranteed to fit within the range of a 32-bit signed integer.
2. You could assume no leading zero bit in the integer’s binary representation.

**Example 1:**

```
Input: 5
Output: 2
Explanation: The binary representation of 5 is 101 (no leading zero bits), and its complement is 010. So you need to output 2.
```

**Example 2:**

```
Input: 1
Output: 0
Explanation: The binary representation of 1 is 1 (no leading zero bits), and its complement is 0. So you need to output 0.
```

## 解析

求一个数的二进制数的补充数字。

转换成二进制之后，全部填1，然后减去原数。

## 代码

``` java
class Solution {
    public int findComplement(int num) {
        int i = 0;
        int j = 0;
        while (i < num) {
            i <<= 1;
            i |= 1;
        }
        return i - num;
    }
}
```