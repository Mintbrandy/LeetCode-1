---
layout: post
title: LeetCode - Maximum Subarray
date: 2017-11-8 19:25:51
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 53. Maximum Subarray

<!--more-->

## 题目

Find the contiguous subarray within an array (containing at least one number) which has the largest sum.

For example, given the array `[-2,1,-3,4,-1,2,1,-5,4]`,
the contiguous subarray `[4,-1,2,1]` has the largest sum = `6`.

More practice:

If you have figured out the O(*n*) solution, try coding another solution using the divide and conquer approach, which is more subtle.

## 解析

求数组中最大连续子串和的值

动态规划问题，讨论区里面一个思路特别好：

To calculate `sum(0,i)`, you have 2 choices: either adding `sum(0,i-1)` to `a[i]`, or not. If `sum(0,i-1)` is negative, adding it to `a[i]`will only make a smaller sum, so we add only if it's non-negative.

```
sum(0,i) = a[i] + (sum(0,i-1) < 0 ? 0 : sum(0,i-1))
```

We can then use O(1) space to keep track of the max sum(0, i) so far.

## 代码

``` java
class Solution {
    public int maxSubArray(int[] nums) {
        int max = nums[0], sum = nums[0];        // 定义初值为数组第一个值
        for (int i = 1; i < nums.length; i++) {  // 从数组第二个值开始
            if (sum < 0) {   // 如果sum < 0，说明nums[i-1]一定是小于零的
                sum = nums[i];  // 最大子序列肯定是不包含nums[i-1]
            } else {
                sum += nums[i];
            }
            max = Math.max(max, sum);
        }
        return max;
    }
}
```