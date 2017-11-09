---
layout: post
title: LeetCode - Remove Duplicates from Sorted List
date: 2017-11-9 22:19:53
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 83. Remove Duplicates from Sorted List

<!--more-->

## 题目

Given a sorted linked list, delete all duplicates such that each element appear only *once*.

For example,
Given `1->1->2`, return `1->2`.
Given `1->1->2->3->3`, return `1->2->3`.

## 解析

删除链表中重复的元素。

下面的第二种方法使用了递归的方法，这里需要思考一个问题，也是在讨论区看见的：

> I highly doubt if we should use recursion in solving linked list problems. We use it for tree because its stack space is O(logn), where n is the number of nodes. But it's O(n) space required for linked list, which is very likely to be stack overflow. Point me out if you hold a different opinion.

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
    public ListNode deleteDuplicates(ListNode head) {
        ListNode list = head;

        while (list != null) {
            if (list.next == null) {
                break;
            }
            if (list.val == list.next.val) {
                list.next = list.next.next;
            } else {
                list = list.next;
            }
        }
        return head;
    }
}
```
```java
public ListNode deleteDuplicates(ListNode head) {
        if(head == null || head.next == null)return head;
        head.next = deleteDuplicates(head.next);
        return head.val == head.next.val ? head.next : head;
}
```