---
layout: post
title: LeetCode - Length of Last Word
date: 2017-11-8 20:19:10
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 58. Length of Last Word

<!--more-->

## 题目

Given a string *s* consists of upper/lower-case alphabets and empty space characters `' '`, return the length of last word in the string.

If the last word does not exist, return 0.

**Note:** A word is defined as a character sequence consists of non-space characters only.

**Example:**

```
Input: "Hello World"
Output: 5
```

## 解析

找到给定字符串中最后一个单词的长度，要是没有就返回 `0`，可以使用`String`里面的`trim()`方法去除前后多余的空格字符等。

## 代码

``` java
class Solution {
    public int lengthOfLastWord(String s) {
        int len = s.length();
        int lastLength = 0; // 初始化为0
        while (len > 0 && s.charAt(len - 1) == ' ') { // 去除结尾的空格
            len--;
        }

        while (len > 0 && s.charAt(len - 1) != ' ') { // 读取最后一个单词
            len--;
            lastLength++;
        }
        return lastLength;
    }
}
```