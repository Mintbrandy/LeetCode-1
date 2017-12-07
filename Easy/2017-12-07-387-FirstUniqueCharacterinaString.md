---
layout: post
title: LeetCode - First Unique Character in a String
date: 2017-12-7 23:43:34
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 387. First Unique Character in a String

<!--more-->

## 题目

Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return -1.

**Examples:**

```
s = "leetcode"
return 0.

s = "loveleetcode",
return 2.

```

**Note:** You may assume the string contain only lowercase letters.

## 解析

找到字符串中，第一个唯一字符的位置。

## 代码

``` java
class Solution {
    public int firstUniqChar(String s) {
        int[] freq = new int[26];
        for (char c : s.toCharArray()) {
            freq[c - 'a']++;
        }
        for (int i = 0; i < s.length(); i++) {
            if (freq[s.charAt(i) - 'a'] == 1) {
                return i;
            }
        }
        return -1;
    }
}
```