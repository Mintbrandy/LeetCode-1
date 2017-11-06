---
layout: post
title: LeetCode - Palindrome Number
date: 2017-11-06
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 9. Palindrome Number

<!--more-->

## 题目

Determine whether an integer is a palindrome. Do this without extra space.

**Some hints:**

Could negative integers be palindromes? (ie, -1)

If you are thinking of converting the integer to string, note the restriction of using extra space.

You could also try reversing an integer. However, if you have solved the problem "Reverse Integer", you know that the reversed integer might overflow. How would you handle such case?

There is a more generic way of solving this problem.

## 解析

判断一个 `int` 型整数是否为回文数字，需要注意，负数不是，不能使用额外的空间，所有不能使用`String`。

可是参考 `Easy - 7. Reverse Integer`，可以计算机到一半进行比较。

## 代码

``` java
class Solution {
    public boolean isPalindrome(int x) {
        if (x < 0 || (x != 0 && x % 10 == 0)) {
            return false;
        }
        int reverse = 0;
        while (x > reverse) {
            reverse = (reverse * 10) + (x % 10);
            x /= 10;
        }
        return (x == reverse || x == reverse / 10);
    }
}
```

