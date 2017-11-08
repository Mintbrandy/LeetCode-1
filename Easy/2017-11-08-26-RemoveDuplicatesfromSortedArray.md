---
layout: post
title: LeetCode - Remove Duplicates from Sorted Array
date: 2017-11-8 08:34:27
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 26. Remove Duplicates from Sorted Array

<!--more-->

## 题目

Given a sorted array, remove the duplicates [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) such that each element appear only *once* and return the new length.

Do not allocate extra space for another array, you must do this by **modifying the input array in-place** with O(1) extra memory.

**Example:**

```
Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.
It doesn't matter what you leave beyond the new length.
```

## 解析

将一个有序数组的重复元素删除，并返回处理后的数组长度。

需要注意的一个地方就是，题目需要在原数组上进行改动，仅仅返回有多少元素不同是不行的。

## 代码

``` java
class Solution {
    public int removeDuplicates(int[] nums) {
        int count = nums.length > 0 ? 1 : 0;
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] != nums[i - 1]) {
                nums[count++] = nums[i];
            }
        }
        return count;
    }
}
```