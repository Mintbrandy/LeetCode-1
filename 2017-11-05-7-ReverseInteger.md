---
layout: post
title: LeetCode - Reverse Integer
date: 2017-11-05
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 7. Reverse Integer

<!--more-->

## 题目

Given a 32-bit signed integer, reverse digits of an integer.

**Example:**

```
Input: 123
Output:  321
```

```
Input: -123
Output: -321
```

```
Input: 120
Output: 21
```

**Note:**

Assume we are dealing with an environment which could only hold integers within the 32-bit signed integer range. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

## 解析

需要注意的是当超出32位有符号整数范围时，输出为0。

## 代码

``` java
class Solution {
    public int reverse(int x) {
        long result = 0;
        while (x != 0) {
            result = result * 10 + (x % 10);
            if (result > Integer.MAX_VALUE || result < Integer.MIN_VALUE)
                return 0;
            x = x / 10;
        }
        return (int) result;
    }
}
```

