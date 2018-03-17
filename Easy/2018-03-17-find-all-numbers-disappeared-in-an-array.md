---
layout: post
title: LeetCode - Find All Numbers Disappeared in an Array
date: 2018-3-17 21:28:17
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 448. Find All Numbers Disappeared in an Array

<!--more-->

## 题目

Given an array of integers where 1 ≤ a[i] ≤ *n* (*n* = size of array), some elements appear twice and others appear once.

Find all the elements of [1, *n*] inclusive that do not appear in this array.

Could you do it without extra space and in O(*n*) runtime? You may assume the returned list does not count as extra space.

**Example:**

```
Input:
[4,3,2,7,8,2,3,1]

Output:
[5,6]
```

## 解析

因为不能使用额外的空间，所以，对于数组，可以将数组的坐标看做一个“额外的空间”

对于数组中已经存在的数字，如果为正，对每一个当做数组下标，并对所在位置数字取负数，这样，如果这个数字为坐标的位置上已经是负数了，就下一个数字，这样将数组中所有出现的数字的坐标位置上的数字全部置换为负数，再进行一次扫描的时候就可以判断没有出现的数字了。

## 代码

``` java
class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        List<Integer> result = new ArrayList<>();

        for (int i = 0; i < nums.length; i++) {
            int val = Math.abs(nums[i]);
            if (nums[val - 1] > 0) {
                nums[val - 1] = -nums[val - 1];
            }
        }
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] > 0) {
                result.add(i + 1);
            }
        }
        return result;
    }
}
```