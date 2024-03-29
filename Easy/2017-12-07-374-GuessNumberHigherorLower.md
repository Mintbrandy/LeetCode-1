---
layout: post
title: LeetCode - Guess Number Higher or Lower
date: 2017-12-7 22:57:57
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 374. Guess Number Higher or Lower

<!--more-->

## 题目

We are playing the Guess Game. The game is as follows:

I pick a number from **1** to **n**. You have to guess which number I picked.

Every time you guess wrong, I'll tell you whether the number is higher or lower.

You call a pre-defined API `guess(int num)` which returns 3 possible results (`-1`, `1`, or `0`):

```
-1 : My number is lower
 1 : My number is higher
 0 : Congrats! You got it!

```

**Example:**

```
n = 10, I pick 6.

Return 6.
```

## 解析

二分查找

## 代码

``` java
/* The guess API is defined in the parent class GuessGame.
   @param num, your guess
   @return -1 if my number is lower, 1 if my number is higher, otherwise return 0
      int guess(int num); */

public class Solution extends GuessGame {
    public int guessNumber(int n) {
        int low = 1;
        int high = n;
        while (low <= high) {
            int mid = low + ((high - low) >>> 1);
            int flag = guess(mid);
            if (flag == 0) {
                return mid;
            } else if (flag < 0) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return -1;
    }
}
```