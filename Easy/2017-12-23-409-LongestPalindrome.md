---
layout: post
title: LeetCode - Longest Palindrome
date: 2017-12-23 13:22:25
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 409. Longest Palindrome

<!--more-->

## 题目

Given a string which consists of lowercase or uppercase letters, find the length of the longest palindromes that can be built with those letters.

This is case sensitive, for example `"Aa"` is not considered a palindrome here.

**Note:**
Assume the length of given string will not exceed 1,010.

**Example:**

```
Input:
"abccccdd"

Output:
7

Explanation:
One longest palindrome that can be built is "dccaccd", whose length is 7.
```

## 解析

判断所给字符串字符，能组成最长回文字符串的长度。

## 代码

``` java
class Solution {
    public int longestPalindrome(String s) {
        int[] lowercase = new int[26];
        int[] uppercase = new int[26];
        int res = 0;
        for (char c : s.toCharArray()) {
            if (c >= 97) lowercase[c - 'a']++;
            else uppercase[c - 'A']++;
        }
        for (int i = 0; i < 26; i++) {
            res += (lowercase[i] / 2) * 2;
            res += (uppercase[i] / 2) * 2;
        }
        return res == s.length() ? res : res + 1;
    }
}
```