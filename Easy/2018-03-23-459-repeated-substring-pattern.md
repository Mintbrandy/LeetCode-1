---
layout: post
title: LeetCode - Repeated Substring Pattern
date: 2018-3-23 16:51:16
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 459. Repeated Substring Pattern

<!--more-->

## 题目

Given a non-empty string check if it can be constructed by taking a substring of it and appending multiple copies of the substring together. You may assume the given string consists of lowercase English letters only and its length will not exceed 10000.

**Example 1:**

```
Input: "abab"

Output: True

Explanation: It's the substring "ab" twice.
```

**Example 2:**

```
Input: "aba"

Output: False
```

**Example 3:**

```
Input: "abcabcabcabc"

Output: True

Explanation: It's the substring "abc" four times. (And the substring "abcabc" twice.)
```

## 解析

其实大家的思路都差不多，首先截取长度能够整除的子串，然后继续判断

这里的方法是使用判断长度，是找到的最高效的方法。

## 代码

``` java
class Solution {
    public boolean repeatedSubstringPattern(String s) {
        if (s == null || s.length() <= 1) {
            return false;
        }
        int n = s.length();

        String repeat;
        for (int len = n / 2; len >= 1; len--) {
            if (n % len == 0) {
                int i = 0;
                repeat = s.substring(0, len);
                while (i <= n - len && s.startsWith(repeat, i)) {
                    i += len;
                }
                if (i == n) {
                    return true;
                }
            }
        }
        return false;
    }
}
```