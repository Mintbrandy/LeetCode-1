---
layout: post
title: LeetCode - Excel Sheet Column Number
date: 2017-11-22 16:05:15
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 171. Excel Sheet Column Number

<!--more-->

## 题目

Related to question [Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/)

Given a column title as appear in an Excel sheet, return its corresponding column number.

For example:

```
    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
```

## 解析

根据给出的列表规则，将字符串转换成数字。与题目 `Easy - 168. Excel Sheet Column Title` 正好相反。

## 代码

``` java
class Solution {
    public int titleToNumber(String s) {
        int result = 0;
        for (char c : s.toCharArray()) {
            result = result * 26 + (c - 'A') + 1;
        }
        return result;
    }
}
```