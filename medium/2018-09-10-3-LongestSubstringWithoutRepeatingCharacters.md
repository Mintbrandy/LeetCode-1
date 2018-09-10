---
layout: post
title: LeetCode - Longest Substring Without Repeating Characters
date: 2018-9-10 10:54:56
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true

---

Medium -  3. Longest Substring Without Repeating Characters

<!--more-->

## 题目

Given a string, find the length of the **longest substring** without repeating characters.

**Example 1:**

```
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", which the length is 3.
```

**Example 2:**

```
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

**Example 3:**

```
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

## 解析

找到最长的不含有重复字符的子串长度

**思路**：转换为找到最长的子串的两个端点的位置，

- 用一个数组保存当前最长子串的起始位置，也就是当前不重复的子串的第一字符的位置；

- 当前字符如果在`start`之后出现，计算一次长度；

- 当前字符如果在`start`之前出现，则后面的指针`end`继续往后走；

  **注意**，此时不需要计算长度，只需要最后比较计算即可。

## 代码

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int maxLength = 0;
        int[] index = new int[128];
        int start = 0;
        int end = 0;
        while (end < s.length()) {
            char c = s.charAt(end);
            if (index[c] > start) {  // 出现重复的时候，先计算end-1和start直接的长度
                if (end - start > maxLength) {
                    maxLength = end - start;
                }
                start = index[c]; // 更新头指针
            } else {    // 如果没出现重复，end向后走
                index[c] = end + 1;
                end++;
            }
        }
        if (end - start > maxLength) {  // 当子串在整体的尾部时，需要再计算一次
            maxLength = end - start;
        }

        return maxLength;
    }
}
```