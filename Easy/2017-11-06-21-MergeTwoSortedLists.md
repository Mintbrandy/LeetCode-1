---
layout: post
title: LeetCode - Merge Two Sorted Lists
date: 2017-11-06 20:55:03
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 21. Merge Two Sorted Lists

<!--more-->

## 题目

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

## 解析

将两个排好序的链表合并

我想，没有比递归更简洁的办法了，也可以使用非递归。

## 代码

``` java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        if (l1 == null) return l2;
        if (l2 == null) return l1;
        if (l1.val < l2.val) {
            l1.next = mergeTwoLists(l1.next, l2);
            return l1;
        } else {
            l2.next = mergeTwoLists(l1, l2.next);
            return l2;
        }
    }
}
```