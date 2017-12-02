---
layout: post
title: LeetCode - Valid Anagram
date: 2017-11-30 13:57:14
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 242. Valid Anagram

<!--more-->

## 题目

Given two strings *s* and *t*, write a function to determine if *t* is an anagram of *s*.

For example,
*s* = "anagram", *t* = "nagaram", return true.
*s* = "rat", *t* = "car", return false.

**Note:**
You may assume the string contains only lowercase alphabets.

**Follow up:**
What if the inputs contain unicode characters? How would you adapt your solution to such case?

## 解析

判断字符串 `t` 是否是 `s` 的“字谜”。

方法一：转换成字符数组，排序，比较

方法二：使用 `hashtable` 映射，再比较

## 代码

``` java
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) {
            return false;
        }
        char[] sArray = s.toCharArray();
        char[] tArray = t.toCharArray();
        Arrays.sort(sArray);
        Arrays.sort(tArray);
        return Arrays.equals(sArray, tArray);
    }
}
```
``` java
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) {
            return false;
        }
        int[] table = new int[26];
        for (int i = 0; i < s.length(); i++) {
            table[s.charAt(i) - 'a']++;
        }
        for (int i = 0; i < t.length(); i++) {
            table[t.charAt(i) - 'a']--;
            if (table[t.charAt(i) - 'a'] < 0) {
                return false;
            }
        }
        return true;
    }
}
```

