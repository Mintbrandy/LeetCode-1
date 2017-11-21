---
layout: post
title: LeetCode - Intersection of Two Linked Lists
date: 2017-11-21 08:52:03
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - Intersection of Two Linked Lists

<!--more-->

## 题目

Write a program to find the node at which the intersection of two singly linked lists begins.

For example, the following two linked lists:

```
A:          a1 → a2
                   ↘
                     c1 → c2 → c3
                   ↗            
B:     b1 → b2 → b3

```

begin to intersect at node c1.

**Notes:**

- If the two linked lists have no intersection at all, return `null`.
- The linked lists must retain their original structure after the function returns.
- You may assume there are no cycles anywhere in the entire linked structure.
- Your code should preferably run in O(n) time and use only O(1) memory.

## 解析

找到两个链表相交的节点。

方法一：使用 `HashSet` 先保存一个链表的所有节点，再去遍历另外一个节点进行查找

方法二：相当于对两个链表遍历了两回，在第一回遍历中，当遍历到末尾节点是，重置当前指针指向另一个链表的头指针，这样，当重置第二个指针时，当前两个指针指向的节点，离末尾节点的距离是一样的，所以第二次遍历时，肯定能找到相同的节点(如果没有相遇节点，相同节点为 `null` )。

## 代码

``` java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if (headA == null || headB == null) {
            return null;
        }

        ListNode a = headA;
        ListNode b = headB;

        while (a != b) {
            a = a == null ? headB : a.next;
            b = b == null ? headA : b.next;
        }
        return a;
    }
}
```