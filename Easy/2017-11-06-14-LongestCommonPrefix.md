---
layout: post
title: LeetCode - Longest Common Prefix
date: 2017-11-6
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 14. Longest Common Prefix

<!--more-->

## 题目

Write a function to find the longest common prefix string amongst an array of strings.

## 解析

求字符串数组的公共最长前缀

先排序，然后就变成求第一个和最后一个的 `longest common prefix`。

## 代码

``` java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs.length == 0) {
            return "";
        }
        StringBuilder result = new StringBuilder();
        Arrays.sort(strs);

        char[] a = strs[0].toCharArray();
        char[] b = strs[strs.length - 1].toCharArray();

        for (int i = 0; i < a.length && i < b.length; i++) {
            if (a[i] == b[i]) {
                result.append(a[i]);
            } else {
                return result.toString();
            }
        }

        return result.toString();
    }
}
```