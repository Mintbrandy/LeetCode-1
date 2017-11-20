---
layout: post
title: LeetCode - Valid Palindrome
date: 2017-11-20 10:30:29
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 125. Valid Palindrome

<!--more-->

## 题目

Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

For example,
`"A man, a plan, a canal: Panama"` is a palindrome.
`"race a car"` is *not* a palindrome.

**Note:**
Have you consider that the string might be empty? This is a good question to ask during an interview.

For the purpose of this problem, we define empty string as valid palindrome.

## 解析

判断字符串是否是回文，忽略标点符号和空格等。

通过两个分别指向头和尾的指针，不断比较，不断移动。

也可以使用正则表达式 `s.replaceAll("[^A-Za-z0-9]", "").toLowerCase();` 将忽略的字符去掉。

## 代码

``` java
class Solution {
    public boolean isPalindrome(String s) {
        if (s.isEmpty()) {
            return true;
        }
        int head = 0;
        int tail = s.length() - 1;
        char cHead, cTail;
        while (head < tail) {
            cHead = s.charAt(head);
            cTail = s.charAt(tail);
            if (!Character.isLetterOrDigit(cHead)) {
                head++;
            } else if (!Character.isLetterOrDigit(cTail)) {
                tail--;
            } else {
                if (Character.toLowerCase(cHead) != Character.toLowerCase(cTail)) {
                    return false;
                }
                head++;
                tail--;
            }
        }
        return true;
    }
}
```