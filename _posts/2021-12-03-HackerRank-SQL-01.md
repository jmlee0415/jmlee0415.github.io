---
title: "[HackerRank] Binary Tree Nodes & New Companies"
date: 2021-12-02T21:31:46+09:00
draft: false
description: "[MySQL] : HackerRank LV - Medium"
tags: [HackerRank]
categories: [MySQL]
toc : true
toc_sticky : true
toc_label : 목차
---
  </br>


<!-- ![image](https://user-images.githubusercontent.com/61037197/147852605-81d63831-6eb7-4733-96d5-6cff152f4909.png)--  -->


```SQL

select N, 
      (case when P is NULL then 'Root' 
            when N in (select P from BST) then 'Inner' 
            else 'Leaf' 
       End) 
from BST order by N

```

```SQL
select tmp.company_code, tmp.founder, tmp.lead_manager_code,tmp.senior_manager_code,
tmp.manager_code, tmp.employee_code 
from (select A.company_code as company_code, ANY_VALUE(founder) as founder, 
count(distinct B.lead_manager_code) as lead_manager_code, count(distinct C.senior_manager_code) as senior_manager_code,
count(distinct D.manager_code) as manager_code, count(distinct E.employee_code) as employee_code from Company as A 
Left Join Lead_Manager as B on A.company_code = B.company_code
Left Join Senior_Manager as C on B.lead_manager_code = C.lead_manager_code
Left Join Manager as D on C.senior_manager_code = D.senior_manager_code
Left Join Employee as E on D.manager_code = E.manager_code group by A.company_code) as tmp ;
```

