---
layout: post
title: LeetCode - Reverse String
date: 2017-12-4 23:16:05
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 344. Reverse String

<!--more-->

## 题目

Write a function that takes a string as input and returns the string reversed.

**Example:**
Given s = "hello", return "olleh".

## 解析

翻转字符串

## 代码

``` java
class Solution {
    public String reverseString(String s) {
        char[] word = s.toCharArray();
        int i = 0;
        int j = s.length()-1;
        while (i < j) {
            char temp = word[i];
            word[i] = word[j];
            word[j] = temp;
            i++;
            j--;
        }
        return new String(word);
    }
}
```