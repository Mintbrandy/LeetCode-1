---
layout: post
title: LeetCode - Valid Parentheses
date: 2017-11-6 20:34:17
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 20. Valid Parentheses

<!--more-->

## 题目

Given a string containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

The brackets must close in the correct order, `"()"` and `"()[]{}"` are all valid but `"(]"` and `"([)]"` are not.

## 解析

经典的括号匹配问题

当扫描到左括号时，将相应的右括号入栈，当扫描到右括号时，取出栈顶元素并比较，不同则表示错误，最后通过栈是否为空进行判断。

## 代码

``` java
class Solution {
    public boolean isValid(String s) {
        LinkedList<Character> stack = new LinkedList<>();
        for (char c : s.toCharArray()) {
            if (c == '(') {
                stack.push(')');
            } else if (c == '{') {
                stack.push('}');
            } else if (c == '[') {
                stack.push(']');
            } else if (stack.isEmpty() || stack.pop() != c) {
                return false;
            }
        }
        return stack.isEmpty();
    }
}
```