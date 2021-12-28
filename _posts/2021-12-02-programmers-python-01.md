---
title: "[PROGRAMMERS] 숫자 문자열과 영단어"
date: 2021-12-02T21:31:46+09:00
draft: false
description: "[PYTHON] : Programmers LV#01 숫자 문자열과 영단어"
tags: [Programmers]
categories: [Algorithm]
toc : true
toc_sticky : true
toc_label : 목차
---
### 문제 설명 </br>

다음은 숫자의 일부 자릿수를 영단어로 바꾸는 예시입니다.

1478 → "one4seveneight" </br>
234567 → "23four5six7"</br>
10203 → "1zerotwozero3"</br>

이렇게 숫자의 일부 자릿수가 영단어로 바뀌어졌거나, 혹은 바뀌지 않고 그대로인 문자열 s가 매개변수로 주어집니다. </br>
s가 의미하는 원래 숫자를 return 하도록 solution 함수를 완성해주세요.

![image](https://user-images.githubusercontent.com/61037197/147594296-363286f7-8ef3-44e6-826d-6952ae5d5ae1.png)


```PYTHON

def solution(s):

    answer = ''
    tmp = ''
    var = {'zero':'0', 'one':'1', 'two':'2', 'three':'3', 'four':'4', 'five':'5', 'six':'6', 'seven':'7', 'eight':'8', 'nine':'9'}
  
    for i in s:
        tmp += i
        if i in list(var.values()): #i = 숫자
            answer += i
            tmp = ''
        elif tmp in var:
            answer += var[tmp]
            tmp = ''
            


    return int(answer)


```
