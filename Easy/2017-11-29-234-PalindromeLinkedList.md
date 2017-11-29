---
layout: post
title: LeetCode - Palindrome Linked List
date: 2017-11-29 16:14:18
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 234. Palindrome Linked List

<!--more-->

## 题目

Given a singly linked list, determine if it is a palindrome.

**Follow up:**
Could you do it in O(n) time and O(1) space?

## 解析

判断一个链表是否是回文的。

先用两个不同速度的指针遍历链表，一个到尾的时候，一个到中点，然后将后半部分翻转，再比较。

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
    public boolean isPalindrome(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        if (fast != null) {
            slow = slow.next;
        }
        slow = reverseList(slow);
        fast = head;
        while (slow != null) {
            if (slow.val != fast.val) {
                return false;
            }
            slow = slow.next;
            fast = fast.next;
        }
        return true;
    }
    
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode curr = head;
        while (curr != null) {
            ListNode nextNode = curr.next;
            curr.next = prev;
            prev = curr;
            curr = nextNode;
        }
        return prev;
    }
}
```