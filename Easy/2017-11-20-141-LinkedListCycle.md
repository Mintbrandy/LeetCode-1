---
layout: post
title: LeetCode - Linked List Cycle
date: 2017-11-20 11:16:27
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 141. Linked List Cycle

<!--more-->

## 题目

Given a linked list, determine if it has a cycle in it.

Follow up:
Can you solve it without using extra space?

## 解析

判断一个链表是否有环。

可以通过 `HashSet` 存储每一个遍历的节点，如果出现相同节点访问两次，说明有环。

还可以通过两个不同的遍历速度去遍历链表，如果有环，肯定会有相遇的节点。

## 代码

``` java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        if(head == null) return false;
        ListNode walker = head;
        ListNode runner = head;
        while (runner.next != null && runner.next.next != null) {
            walker = walker.next;
            runner = runner.next.next;
            if (walker == runner) return true;
        }
        return false;
    }
}
```