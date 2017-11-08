---
layout: post
title: LeetCode - Count and Say
date: 2017-11-8 10:49:35
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 38. Count and Say

<!--more-->

## 题目

The count-and-say sequence is the sequence of integers with the first five terms as following:

```
1.     1
2.     11
3.     21
4.     1211
5.     111221
```

`1` is read off as `"one 1"` or `11`.
`11` is read off as `"two 1s"` or `21`.
`21` is read off as `"one 2`, then `one 1"` or `1211`.

Given an integer *n*, generate the *n*th term of the count-and-say sequence.

Note: Each term of the sequence of integers will be represented as a string.

**Example:**

```
Input: 1
Output: "1"
```

```
Input: 4
Output: "1211"
```



## 解析

题目比较难理解

下一行字符串是上一个的解释说明，这样再去看题目就容易理解了，类似于一个迭代的过程，要注意两个`for`循环是从`1`开始的。

## 代码

``` java
class Solution {
    public String countAndSay(int n) {
        StringBuilder result = new StringBuilder("1");
        for (int outer = 1; outer < n; outer++) {
            String prev = result.toString();
            result = new StringBuilder();
            int count = 1;
            char say = prev.charAt(0);

            for (int i = 1; i < prev.length(); i++) {
                if (prev.charAt(i) != say) {
                    result.append(count).append(say);
                    count = 1;
                    say = prev.charAt(i);
                } else {
                    count++;
                }
            }
            result.append(count).append(say);
        }
        return result.toString();
    }
}
```