---
layout: post
title: LeetCode - Pascal's Triangle
date: 2017-11-17 20:27:10
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 118. Pascal's Triangle

<!--more-->

## 题目

Given *numRows*, generate the first *numRows* of Pascal's triangle.

For example, given *numRows* = 5,
Return

```
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```

## 解析

生成杨辉三角

`result.add(new ArrayList<>(row));` 这个地方需要注意，传入一个克隆的 `ArrayList` ，后面变化 `row` 的时候保证不会引起变化。

## 代码

``` java
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> result = new ArrayList<>();
        ArrayList<Integer> row = new ArrayList<>();
        for (int i = 0; i < numRows; i++) {
            row.add(0, 1);
            for (int j = 1; j < row.size() - 1; j++) {
                row.set(j, row.get(j) + row.get(j + 1));
            }
            result.add(new ArrayList<>(row));
        }
        return result;
    }
}
```