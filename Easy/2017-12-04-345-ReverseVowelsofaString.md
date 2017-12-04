---
layout: post
title: LeetCode - Reverse Vowels of a String
date: 2017-12-4 23:31:11
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 345. Reverse Vowels of a String

<!--more-->

## 题目

Write a function that takes a string as input and reverse only the vowels of a string.

**Example 1:**
Given s = "hello", return "holle".

**Example 2:**
Given s = "leetcode", return "leotcede".

**Note:**
The vowels does not include the letter "y".

## 解析

翻转元音字母？我都不知道什么是元音。。。

和 `Easy - 344. Reverse String` 是一样的

## 代码

``` java
class Solution {
    public String reverseVowels(String s) {
        if (s == null || s.length() == 0) return s;
        String vowels = "aeiouAEIOU";
        char[] chars = s.toCharArray();
        int start = 0;
        int end = s.length() - 1;
        while (start < end) {
            while (start < end && vowels.indexOf(chars[start]) == -1) {
                start++;
            }
            while (start < end && vowels.indexOf(chars[end]) == -1) {
                end--;
            }

            char temp = chars[start];
            chars[start] = chars[end];
            chars[end] = temp;

            start++;
            end--;
        }
        return new String(chars);
    }
}
```