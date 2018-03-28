---
layout: post
title: LeetCode - Hamming Distance
date: 2018-3-28 16:09:15
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 461. Hamming Distance

<!--more-->

## 题目

The [Hamming distance](https://en.wikipedia.org/wiki/Hamming_distance) between two integers is the number of positions at which the corresponding bits are different.

Given two integers `x` and `y`, calculate the Hamming distance.

**Note:**
0 ≤ `x`, `y` < 231.

**Example:**

```
Input: x = 1, y = 4

Output: 2

Explanation:
1   (0 0 0 1)
4   (0 1 0 0)
       ↑   ↑

The above arrows point to positions where the corresponding bits are different.
```

## 解析

计算两个数，二进制不同的位数。

## 代码

``` java
class Solution {
    public int hammingDistance(int x, int y) {
        int n = x ^ y;
        int count = 0;
        //也可以使用Integer.bitCount(x^y)；
        while (n != 0) {
            n = n & (n - 1);
            count++;
        }
        return count;
    }
}
```