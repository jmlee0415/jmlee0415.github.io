---
title: "[HackerRank] Binary Tree Nodes"
date: 2021-12-02T21:31:46+09:00
draft: false
description: "[MySQL] : HackerRank Intermediate"
tags: [HackerRank]
categories: [MySQL]
toc : true
toc_sticky : true
toc_label : 목차
---
### Sample Input & Output  </br>


![image](https://user-images.githubusercontent.com/61037197/147852605-81d63831-6eb7-4733-96d5-6cff152f4909.png)


```SQL

select N, 
      (case when P is NULL then 'Root' 
            when N in (select P from BST) then 'Inner' 
            else 'Leaf' 
       End) 
from BST order by N

```
