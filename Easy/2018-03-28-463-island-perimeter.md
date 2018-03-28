---
layout: post
title: LeetCode - Island Perimeter
date: 2018-3-28 16:22:42
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 463. Island Perimeter

<!--more-->

## 题目

You are given a map in form of a two-dimensional integer grid where 1 represents land and 0 represents water. Grid cells are connected horizontally/vertically (not diagonally). The grid is completely surrounded by water, and there is exactly one island (i.e., one or more connected land cells). The island doesn't have "lakes" (water inside that isn't connected to the water around the island). One cell is a square with side length 1. The grid is rectangular, width and height don't exceed 100. Determine the perimeter of the island.

**Example:**

```
[[0,1,0,0],
 [1,1,1,0],
 [0,1,0,0],
 [1,1,0,0]]

Answer: 16
Explanation: The perimeter is the 16 yellow stripes in the image below:
```

![](https://leetcode.com/static/images/problemset/island.png)

## 解析

求周长

## 代码

``` java
class Solution {
    public int islandPerimeter(int[][] grid) {
        int total = 0;
        for(int i = 0; i < grid.length; i++){
            for(int j = 0; j < grid[i].length; j++){
                if(grid[i][j] == 1){
                    if(i == 0 || grid[i-1][j] == 0){
                        total += 1;
                    }
                    if(j == 0 || grid[i][j-1] == 0){
                        total += 1;
                    }
                }
            }
        }
        return total*2;
    }
}
```