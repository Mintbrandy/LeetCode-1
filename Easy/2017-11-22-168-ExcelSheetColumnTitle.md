---
layout: post
title: LeetCode - Excel Sheet Column Title
date: 2017-11-22 14:55:16
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 168. Excel Sheet Column Title

<!--more-->

## 题目

Given a positive integer, return its corresponding column title as appear in an Excel sheet.

For example:

```
    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 
```

## 解析

根据所给的列表规则，将一个数字装换成字符串。因为 `A` 是从 `1` 开始的，所有每次循环时，都要先 `--n` 。

## 代码

``` java
class Solution {
    public String convertToTitle(int n) {
        StringBuilder result = new StringBuilder();
        while (n > 0) {
            n--;     // 因为A是从1开始的，所以要先将n-1
            result.append((char) ('A' + n % 26));
            n /= 26;
        }
        return result.reverse().toString();
    }
}
```