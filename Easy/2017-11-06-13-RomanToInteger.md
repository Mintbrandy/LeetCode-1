---
layout: post
title: LeetCode - Roman to Integer
date: 2017-11-06
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 13. Roman to Integer

<!--more-->

## 题目

Given a roman numeral, convert it to an integer.

Input is guaranteed to be within the range from 1 to 3999.

## 解析

首先，了解一下[罗马数字的规则](https://www.douban.com/note/335254352/)

最主要的是每个字母代表的数字大小 `I（1）、V（5）、X（10）、L（50）、C（100）、D（500）和M（1000）`

和两条规则：

```
1 在较大的罗马数字的右边记上较小的罗马数字，表示大数字加小数字。
2 在较大的罗马数字的左边记上较小的罗马数字，表示大数字减小数字。
```

## 代码

``` java
class Solution {
    public int romanToInt(String s) {
        int len = s.length();
        if (len == 0) {
            return -1;
        }
        Map<Character, Integer> map = new HashMap<>();
        map.put('I', 1);
        map.put('V', 5);
        map.put('X', 10);
        map.put('L', 50);
        map.put('C', 100);
        map.put('D', 500);
        map.put('M', 1000);

        int result = map.get(s.charAt(len - 1));
        for (int i = len - 2; i >= 0; i--) {
            if (map.get(s.charAt(i)) >= map.get(s.charAt(i + 1))) {
                result += map.get(s.charAt(i));
            } else {
                result -= map.get(s.charAt(i));
            }
        }
        return result;
    }
}
```

