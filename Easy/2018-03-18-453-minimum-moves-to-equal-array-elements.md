---
layout: post
title: LeetCode - Minimum Moves to Equal Array Elements
date: 2018-3-18 09:50:04
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 453. Minimum Moves to Equal Array Elements

<!--more-->

## 题目

Given a **non-empty** integer array of size *n*, find the minimum number of moves required to make all array elements equal, where a move is incrementing *n* - 1 elements by 1.

**Example:**

```
Input:
[1,2,3]

Output:
3

Explanation:
Only three moves are needed (remember each move increments two elements):

[1,2,3]  =>  [2,3,3]  =>  [3,4,3]  =>  [4,4,4]
```

## 解析

一个数学题

设数组总和为sum，最小的数字为min，需要的步数为m，最后数组数字全部变成x

`sum + m * (n-1) = x * n`

`x = min + m`

由上面两个式子可以得到 `m = sum - min * n`

## 代码

``` java
class Solution {
    public int minMoves(int[] nums) {
        int min = nums[0];
        int sum = 0;
        for (int num : nums) {
            sum += num;
            min = min < num ? min : num;
        }
        return sum - min * nums.length;
    }
}
```
