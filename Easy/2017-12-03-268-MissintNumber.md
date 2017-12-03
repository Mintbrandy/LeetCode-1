---
layout: post
title: LeetCode - Missing Number
date: 2017-12-3 22:32:05
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 268. Missing Number

<!--more-->

## 题目

Given an array containing *n* distinct numbers taken from `0, 1, 2, ..., n`, find the one that is missing from the array.

**Example 1**

```
Input: [3,0,1]
Output: 2

```

**Example 2**

```
Input: [9,6,4,2,3,5,7,0,1]
Output: 8

```

**Note**:
Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity?

## 解析

找到缺失的元素

## 代码

``` java
class Solution {
    public int missingNumber(int[] nums) {
        int sum = 0;
        int n = nums.length;
        for (int num : nums) {
            sum += num;
        }
        return ((n * (1 + n)) >>> 1) - sum;
    }
}
```
``` java
class Solution {
    public int missingNumber(int[] nums) {
        int result = nums.length;
        for (int i = 0; i < nums.length; i++) {
            result ^= i ^ nums[i];
        }
        return result;
    }
}
```

