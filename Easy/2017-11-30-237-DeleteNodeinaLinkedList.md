---
layout: post
title: LeetCode - Delete Node in a Linked List
date: 2017-11-30 13:38:35
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 237. Delete Node in a Linked List

<!--more-->

## 题目

Write a function to delete a node (except the tail) in a singly linked list, given only access to that node.

Supposed the linked list is `1 -> 2 -> 3 -> 4` and you are given the third node with value `3`, the linked list should become `1 -> 2 -> 4` after calling your function.

## 解析

删除链表中给出节点的元素，复制下一个节点，然后删除下一个节点。

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
    public void deleteNode(ListNode node) {
        node.val = node.next.val;
        node.next = node.next.next;
    }
}
```