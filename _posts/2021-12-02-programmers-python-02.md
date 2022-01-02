---
title: "[PROGRAMMERS] 완주하지 못한 선수"
date: 2021-12-03T21:31:46+09:00
draft: false
description: "[PYTHON] : Programmers LV#01 "
tags: [Programmers]
categories: [Algorithm]
toc : true
toc_sticky : true
toc_label : 목차
---

<문제> </br>
![image](https://user-images.githubusercontent.com/61037197/147883865-fb7d67af-0d52-4218-a625-5973f47bfb9d.png)


```PYTHON
def solution(participant, completion):
    
    participant.sort()
    completion.sort()

    for i in range(0, len(completion)):
        if participant[i] != completion[i]:
            return participant[i]
            
    return participant[-1]
```
