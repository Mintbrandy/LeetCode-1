---
layout: post
title: LeetCode - Combine Two Tables
date: 2017-11-23 10:29:18
categories: LeetCode
tags: LeetCode
author: renshuo
mathjax: true
---

Easy - 175. Combine Two Tables

<!--more-->

## 题目

Table: `Person`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| PersonId    | int     |
| FirstName   | varchar |
| LastName    | varchar |
+-------------+---------+
PersonId is the primary key column for this table.

```

Table: `Address`

```
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| AddressId   | int     |
| PersonId    | int     |
| City        | varchar |
| State       | varchar |
+-------------+---------+
AddressId is the primary key column for this table.

```

Write a SQL query for a report that provides the following information for each person in the Person table, regardless if there is an address for each of those people:

```
FirstName, LastName, City, State
```

## 解析

SQL语句，联合查询

## 代码

``` sql
# Write your MySQL query statement below
select FirstName, LastName, City, State from Person left join Address on Person.PersonId = Address.PersonId;
```