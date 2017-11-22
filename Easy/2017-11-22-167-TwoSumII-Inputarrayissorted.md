---
layout: post
title: LeetCode - Two Sum II - Input array is sorted
date: 2017-11-22 14:22:19
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 167. Two Sum II - Input array is sorted

<!--more-->

## 题目

Given an array of integers that is already **sorted in ascending order**, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2. Please note that your returned answers (both index1 and index2) are not zero-based.

You may assume that each input would have *exactly* one solution and you may not use the *same* element twice.

**Input:** numbers={2, 7, 11, 15}, target=9
**Output:** index1=1, index2=2

## 解析

在一个有序数组中，找到两个数，使他们的和与给定值相同，并返回它们所在数组的位置。

使用两个指针，一个指向头，一个指向尾，通过他们的和与给定值的比较，判断指针的移动。

## 代码

``` java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int start = 0;
        int end = numbers.length - 1;
        while (start < end) {
            int sum = numbers[start] + numbers[end];
            if (sum == target) {
                break;
            } else if (sum > target) {
                end--;
            } else {
                start++;
            }
        }
        return new int[]{start + 1, end + 1};
    }
}
```