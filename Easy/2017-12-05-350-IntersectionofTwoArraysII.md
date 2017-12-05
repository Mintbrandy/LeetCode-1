---
layout: post
title: LeetCode - Intersection of Two Arrays II
date: 2017-12-5 23:36:40
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 350. Intersection of Two Arrays II

<!--more-->

## 题目

Given two arrays, write a function to compute their intersection.

**Example:**
Given *nums1* = `[1, 2, 2, 1]`, *nums2* = `[2, 2]`, return `[2, 2]`.

**Note:**

- Each element in the result should appear as many times as it shows in both arrays.
- The result can be in any order.

**Follow up:**

- What if the given array is already sorted? How would you optimize your algorithm?
- What if *nums1*'s size is small compared to *nums2*'s size? Which algorithm is better?
- What if elements of *nums2* are stored on disk, and the memory is limited such that you cannot load all elements into the memory at once?

## 解析

求解两个数组的相同元素，返回可以有重复

## 代码

``` java
class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        Arrays.sort(nums1);
        Arrays.sort(nums2);
        int pnt1 = 0;
        int pnt2 = 0;
        ArrayList<Integer> myList = new ArrayList<>();
        while ((pnt1 < nums1.length) && (pnt2 < nums2.length)) {
            if (nums1[pnt1] < nums2[pnt2]) {
                pnt1++;
            } else if (nums1[pnt1] > nums2[pnt2]) {
                pnt2++;
            } else {
                myList.add(nums1[pnt1]);
                pnt1++;
                pnt2++;
            }
        }
        int[] res = new int[myList.size()];
        for (int i = 0; i < res.length; i++) {
            res[i] = myList.get(i);
        }
        return res;
    }
}
```