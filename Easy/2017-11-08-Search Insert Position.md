---
layout: post
title: LeetCode - Search Insert Position
date: 2017-11-8 09:55:06
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 35. Search Insert Position

<!--more-->

## 题目

Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

**Example:**

```
Input: [1,3,5,6], 5
Output: 2
```

```
Input: [1,3,5,6], 2
Output: 1
```

```
Input: [1,3,5,6], 7
Output: 4
```

```
Input: [1,3,5,6], 0
Output: 0
```



## 解析

查找数组中，所给元素应当插入的位置，如果数组中已有该元素，返回所在位置

二分查找

## 代码

``` java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int low = 0;
        int high = nums.length - 1;
        while (low <= high) {
            int mid = (low + high) >>> 1;
            if (nums[mid] == target) {
                return mid;
            } else if (nums[mid] > target) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return low;
    }
}
```