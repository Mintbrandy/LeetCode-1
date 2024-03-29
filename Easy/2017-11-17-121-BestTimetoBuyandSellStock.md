---
layout: post
title: LeetCode - Best Time to Buy and Sell Stock
date: 2017-11-17 22:20:53
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 121. Best Time to Buy and Sell Stock

<!--more-->

## 题目

Say you have an array for which the *i* ^th^ element is the price of a given stock on day *i*.

If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.

**Example 1:**

```
Input: [7, 1, 5, 3, 6, 4]
Output: 5

max. difference = 6-1 = 5 (not 7-1 = 6, as selling price needs to be larger than buying price)

```

**Example 2:**

```
Input: [7, 6, 4, 3, 1]
Output: 0

In this case, no transaction is done, i.e. max profit = 0.
```

## 解析

从讨论区找了一个特别好的思路

The logic to solve this problem is same as "max subarray problem" using `Kadane's Algorithm`. Since no body has mentioned this so far, I thought it's a good thing for everybody to know.

All the straight forward solution should work, but if the interviewer twists the question slightly by giving the **difference array of prices**, Ex: for `{1, 7, 4, 11}`, if he gives `{0, 6, -3, 7}`, you might end up being confused.

Here, the logic is to calculate the difference (`maxCur += prices[i] - prices[i-1]`) of the original array, and find a contiguous subarray giving maximum profit. If the difference falls below 0, reset it to zero.

```
    public int maxProfit(int[] prices) {
        int maxCur = 0, maxSoFar = 0;
        for(int i = 1; i < prices.length; i++) {
            maxCur = Math.max(0, maxCur += prices[i] - prices[i-1]);
            maxSoFar = Math.max(maxCur, maxSoFar);
        }
        return maxSoFar;
    }

```

*`maxCur = current maximum value`

*`maxSoFar = maximum value found so far`

## 代码

``` java
class Solution {
    public int maxProfit(int[] prices) {
        int maxCur = 0, maxSofar = 0;
        for (int i = 1; i < prices.length; i++) {
            maxCur = Math.max(0, maxCur + (prices[i] - prices[i - 1]));
            maxSofar = Math.max(maxCur, maxSofar);
        }
        return maxSofar;
    }
}
```