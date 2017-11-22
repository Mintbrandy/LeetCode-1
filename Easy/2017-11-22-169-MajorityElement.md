---
layout: post
title: LeetCode - Majority Element
date: 2017-11-22 15:27:46
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 169. Majority Element

<!--more-->

## 题目

Given an array of size *n*, find the majority element. The majority element is the element that appears **more than** `⌊ n/2 ⌋` times.

You may assume that the array is non-empty and the majority element always exist in the array.

## 解析

找到数组中的主元素，主元素在数组中的个数大于数组程度的一半。从左到右扫面数组，如果当前元素 `ai` 是主元素，那么，从当前位置 `i` 开始一直到数组结束，当前元素出现的个数肯定大于 `i` 到 `end` 长度的一半。

更详细的解析请看官方解决办法。

## 代码

``` java
class Solution {
    public int majorityElement(int[] nums) {
        int count = 1;
        int result = nums[0];
        for (int i = 1; i < nums.length; i++) {
            if (count == 0) {
                result = nums[i];
            }
            count += (nums[i] == result ? 1 : -1);
        }
        return result;
    }
}
```