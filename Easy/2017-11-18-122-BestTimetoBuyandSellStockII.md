---
layout: post
title: LeetCode - Best Time to Buy and Sell Stock II
date: 2017-11-18 09:30:12
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 122. Best Time to Buy and Sell Stock II

<!--more-->

## 题目

Say you have an array for which the *i*th element is the price of a given stock on day *i*.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (ie, buy one and sell one share of the stock multiple times). However, you may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).

## 解析

买股票问题，多次交易，求最大获利值。**注意：** *在卖出股票之前是不能再次购买的*

将每个“股票上升”获得的利益相加，`total += prices[i + 1] - prices[i];` 这个语句某种程度上实现了拼接操作，例如 `[3, 4, 5]`，`(4 - 3) + (5 - 4) = (5-3)` 

## 代码

``` java
class Solution {
    public int maxProfit(int[] prices) {
        int total = 0;
        for (int i = 0; i < prices.length - 1; i++) {
            if (prices[i + 1] > prices[i]) {
                total += prices[i + 1] - prices[i];
            }
        }
        return total;
    }
}
```