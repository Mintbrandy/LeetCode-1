---
layout: post
title: LeetCode - Implement strStr()
date: 2017-11-8 09:15:06
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 28. Implement strStr()

<!--more-->

## 题目

Implement [strStr()](http://www.cplusplus.com/reference/cstring/strstr/).

Return the index of the first occurrence of needle in haystack, or **-1** if needle is not part of haystack.

**Example:**

```
Input: haystack = "hello", needle = "ll"
Output: 2
```

```
Input: haystack = "aaaaa", needle = "bba"
Output: -1
```



## 解析

获得字符串中第一次出现目标字符串的位置，有兴趣的可以去看一下 `String` 的`indexOf()`方法。

## 代码

``` java
class Solution {
    public int strStr(String haystack, String needle) {
        return haystack.indexOf(needle);
    }
}
```