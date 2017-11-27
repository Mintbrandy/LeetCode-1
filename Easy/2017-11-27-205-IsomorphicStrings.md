---
layout: post
title: LeetCode - Isomorphic Strings
date: 2017-11-27 08:46:28
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 205. Isomorphic Strings

<!--more-->

## 题目

Given two strings **s** and **t**, determine if they are isomorphic.

Two strings are isomorphic if the characters in **s** can be replaced to get **t**.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character but a character may map to itself.

For example,
Given `"egg"`, `"add"`, return true.

Given `"foo"`, `"bar"`, return false.

Given `"paper"`, `"title"`, return true.

**Note:**
You may assume both **s** and **t** have the same length.

## 解析

判断两个字符串是否同构，因为 `ASCII` 码一共有 `256` 个，所以使用数组分别保存两个字符串之间的映射关系。

另一种方法是保存上一次出现同样字符的位置，进行比较。

## 代码

``` java
class Solution {
    public boolean isIsomorphic(String s, String t) {
        if (s.length() != t.length())
            return false;

        char[] sm = new char[256];
        char[] tm = new char[256];

        for (int i = 0; i < s.length(); i++) {
            char sc = s.charAt(i);
            char tc = t.charAt(i);
            if (sm[sc] == 0 && tm[tc] == 0) {
                sm[sc] = tc;
                tm[tc] = sc;
            } else {
                if (sm[sc] != tc || tm[tc] != sc) {
                    return false;
                }
            }
        }
        return true;
    }
}
```
``` java
class Solution {
    public boolean isIsomorphic(String s, String t) {
        if (s.length() != t.length())
            return false;
        int[] ms = new int[256];
        int[] mt = new int[256];
        for (int i = 0; i < s.length(); i++) {
            if (ms[s.charAt(i)] != mt[t.charAt(i)]) {
                return false;
            }
            ms[s.charAt(i)] = mt[t.charAt(i)] = i + 1;
        }
        return true;
    }
}
```

