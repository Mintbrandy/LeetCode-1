---
layout: post
title: LeetCode - Remove Linked List Elements
date: 2017-11-25 22:04:08
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 203. Remove Linked List Elements

<!--more-->

## 题目

Remove all elements from a linked list of integers that have value **val**.

**Example**
*Given:* 1 --> 2 --> 6 --> 3 --> 4 --> 5 --> 6, **val** = 6
*Return:* 1 --> 2 --> 3 --> 4 --> 5

## 解析

去除链表中与给定值相同的所有节点。

需要考虑，当头结点需要删除的情况。

方法一：使用递归

方法二：使用一个假的头结点，比方法一快

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
    public ListNode removeElements(ListNode head, int val) {
        if (head == null) return null;
        head.next = removeElements(head.next, val);
        return head.val == val ? head.next : head;
    }
}
```
``` java
class Solution {
    public ListNode removeElements(ListNode head, int val) {
        ListNode fakeHead = new ListNode(-1);
        fakeHead.next = head;
        ListNode curr = head, prev = fakeHead;
        while (curr != null) {
            if (curr.val == val) {
                prev.next = curr.next;
            } else {
                prev = prev.next;
            }
            curr = curr.next;
        }
        return fakeHead.next;
    }
}
```

