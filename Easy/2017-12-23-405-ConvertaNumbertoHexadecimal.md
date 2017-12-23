---
layout: post
title: LeetCode - Convert a Number to Hexadecimal
date: 2017-12-23 13:02:02
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 405. Convert a Number to Hexadecimal

<!--more-->

## 题目

Given an integer, write an algorithm to convert it to hexadecimal. For negative integer, [two’s complement](https://en.wikipedia.org/wiki/Two%27s_complement) method is used.

**Note:**

1. All letters in hexadecimal (`a-f`) must be in lowercase.
2. The hexadecimal string must not contain extra leading `0`s. If the number is zero, it is represented by a single zero character `'0'`; otherwise, the first character in the hexadecimal string will not be the zero character.
3. The given number is guaranteed to fit within the range of a 32-bit signed integer.
4. You **must not use any method provided by the library** which converts/formats the number to hex directly.

**Example 1:**

```
Input:
26

Output:
"1a"

```

**Example 2:**

```
Input:
-1

Output:
"ffffffff"
```

## 解析

将十进制转换成16进制。类似于 `Integer.toHexString(int i)` 方法。

## 代码

``` java
class Solution {
    public String toHex(int num) {
        StringBuilder sb = new StringBuilder();
        do {
            int n = num & 0xf;  // 每次获取后四位
            n += n < 0xa ? '0' : 'a' - 10;
            sb.append((char) n);
        } while ((num >>>= 4) != 0);
        return sb.reverse().toString();
    }
}
```