---
layout: post
title: LeetCode - Implement Queue using Stacks
date: 2017-11-29 11:13:12
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 232. Implement Queue using Stacks

<!--more-->

## 题目

Implement the following operations of a queue using stacks.

- push(x) -- Push element x to the back of queue.
- pop() -- Removes the element from in front of queue.
- peek() -- Get the front element.
- empty() -- Return whether the queue is empty.

Notes:

- You must use *only* standard operations of a stack -- which means only `push to top`, `peek/pop from top`, `size`, and `is empty` operations are valid.
- Depending on your language, stack may not be supported natively. You may simulate a stack by using a list or deque (double-ended queue), as long as you use only standard operations of a stack.
- You may assume that all operations are valid (for example, no pop or peek operations will be called on an empty queue).

## 解析

使用栈实现队列，在 `java.util.Stack` 的源码中，建议使用 `java.util.Deque` 代替栈操作。

## 代码

``` java
class MyQueue {

    Deque<Integer> s1 = new ArrayDeque<>();
    Deque<Integer> s2 = new ArrayDeque<>();

    /**
     * Initialize your data structure here.
     */
    public MyQueue() {
        s1.clear();
        s2.clear();
    }

    /**
     * Push element x to the back of queue.
     */
    public void push(int x) {
        while (!s2.isEmpty()) {
            s1.push(s2.pop());
        }
        s1.push(x);
    }

    /**
     * Removes the element from in front of queue and returns that element.
     */
    public int pop() {
        while (!s1.isEmpty()) {
            s2.push(s1.pop());
        }
        return s2.pop();
    }

    /**
     * Get the front element.
     */
    public int peek() {
        while (!s1.isEmpty()) {
            s2.push(s1.pop());
        }
        return s2.peek();
    }

    /**
     * Returns whether the queue is empty.
     */
    public boolean empty() {
        return s1.isEmpty() && s2.isEmpty();
    }
}
/**
 * Your MyQueue object will be instantiated and called as such:
 * MyQueue obj = new MyQueue();
 * obj.push(x);
 * int param_2 = obj.pop();
 * int param_3 = obj.peek();
 * boolean param_4 = obj.empty();
 */
```