---
layout: post
title: LeetCode - Pascal's Triangle II
date: 2017-11-17 21:53:02
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 119. Pascal's Triangle II

<!--more-->

## 题目

Given an index *k*, return the *k*th row of the Pascal's triangle.

For example, given *k* = 3,
Return `[1,3,3,1]`.

**Note:**
Could you optimize your algorithm to use only *O*(*k*) extra space?

## 解析

输出杨辉三角的第 `k` 行，参考 `Easy - 118. Pascal's Triangle` 这道题的解决办法。

## 代码

``` java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> row = new ArrayList<>();
        for (int i = 0; i <= rowIndex; i++) {
            row.add(0, 1);
            for (int j = 1; j < row.size() - 1; j++) {
                row.set(j, row.get(j) + row.get(j + 1));
            }
        }
        return row;
    }
}
```