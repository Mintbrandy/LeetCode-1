---
layout: post
title: LeetCode - Third Maximum Number
date: 2018-3-14 20:21:34
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 414. Third Maximum Number

<!--more-->

## 题目

Given a **non-empty** array of integers, return the **third** maximum number in this array. If it does not exist, return the maximum number. The time complexity must be in O(n).

**Example 1:**

```
Input: [3, 2, 1]

Output: 1

Explanation: The third maximum is 1.
```

**Example 2:**

```
Input: [1, 2]

Output: 2

Explanation: The third maximum does not exist, so the maximum (2) is returned instead.
```

**Example 3:**

```
Input: [2, 2, 3, 1]

Output: 1

Explanation: Note that the third maximum here means the third maximum distinct number.
Both numbers with value 2 are both considered as second maximum.
```

## 解析

找到一个数组中，第三大的数

## 代码

``` java
class Solution {
    public int thirdMax(int[] nums) {
        long first = Long.MIN_VALUE;
        long second = Long.MIN_VALUE;
        long third = Long.MIN_VALUE;
        for (int i : nums) {
            if (i > first) {
                third = second;
                second = first;
                first = i;
            } else if (i == first) {
            } else if (i > second) {
                third = second;
                second = i;
            } else if (i == second) {
            } else if (i > third) {
                third = i;
            }
        }
        return third == Long.MIN_VALUE ? (int) first : (int) third;
    }
}
```