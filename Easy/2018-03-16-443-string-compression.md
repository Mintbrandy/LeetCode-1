---
layout: post
title: LeetCode - String Compression
date: 2018-3-16 20:12:54
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 443. String Compression

<!--more-->

## 题目

Given an array of characters, compress it [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm).

The length after compression must always be smaller than or equal to the original array.

Every element of the array should be a **character** (not int) of length 1.

After you are done **modifying the input array in-place**, return the new length of the array.

**Follow up:**
Could you solve it using only O(1) extra space?

**Example 1:**

```
Input:
["a","a","b","b","c","c","c"]

Output:
Return 6, and the first 6 characters of the input array should be: ["a","2","b","2","c","3"]

Explanation:
"aa" is replaced by "a2". "bb" is replaced by "b2". "ccc" is replaced by "c3".
```

**Example 2:**

```
Input:
["a"]

Output:
Return 1, and the first 1 characters of the input array should be: ["a"]

Explanation:
Nothing is replaced.
```

**Example 3:**

```
Input:
["a","b","b","b","b","b","b","b","b","b","b","b","b"]

Output:
Return 4, and the first 4 characters of the input array should be: ["a","b","1","2"].

Explanation:
Since the character "a" does not repeat, it is not compressed. "bbbbbbbbbbbb" is replaced by "b12".
Notice each digit has it's own entry in the array.
```

**Note:**

1. All characters have an ASCII value in `[35, 126]`.
2. `1 <= len(chars) <= 1000`.

## 解析

压缩字符数组，注意，虽然java里面是参数传递是传值，但是数组修改的时候还是会影响到原数组的。

## 代码

``` java
class Solution {
    public int compress(char[] chars) {
        int anchor = 0; // 记录旧数组中，第一个不被压缩字符的位置
        int writer = 0; // 记录新数组指针
        for (int i = 0; i < chars.length; i++) {
            // 如果到末尾位置，或者前后两个字符不同
            if (i + 1 == chars.length || chars[i] != chars[i + 1]) {
                // 此时，将之前全部相同字符压缩
                chars[writer++] = chars[anchor];
                // 当被压缩字符数量大于1时
                if (i > anchor) {
                    // 将数字转换成字符数组
                    for (char c : ("" + (i - anchor + 1)).toCharArray()) {
                        chars[writer++] = c;
                    }
                }
                // 指向下一个字符
                anchor = i + 1;
            }
        }
        return writer;
    }
}
```