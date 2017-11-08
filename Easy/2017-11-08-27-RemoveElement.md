---
layout: post
title: LeetCode - Remove Element
date: 2017-11-8 08:54:16
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 27. Remove Element

<!--more-->

## 题目

Given an array and a value, remove all instances of that value [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) and return the new length.

Do not allocate extra space for another array, you must do this by **modifying the input array in-place** with O(1) extra memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

**Example:**

```
Given nums = [3,2,2,3], val = 3,

Your function should return length = 2, with the first two elements of nums being 2.
```



## 解析

删除数组中与所给元素相同的值，返回处理后的数组长度。

## 代码

``` java
class Solution {
    public int removeElement(int[] nums, int val) {
        int count = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != val) {
                nums[count++] = nums[i];
            }
        }
        return count;
    }
}
```