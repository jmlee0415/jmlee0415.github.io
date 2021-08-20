---
title: "trueskill 공부"
date: 2021-06-01T21:31:46+09:00
draft: false
description: "논문을 바탕으로 trueskill 이해하기 "
tags: [Study]
categories: [Study]
toc : true
toc_sticky : true
toc_label : 목차
---



## :octocat: Trueskill 이란..?

Trueskill system은 간단히 말해 마이크로소프트가 출시한 '멀티플레이어 랭킹 시스템'이다! </br>
Tureskill systmem의 이해를 돕기 위해 우선 ELO 랭킹 시스템을 먼저 알아볼 필요가 있다.  </br>


### :eyes: ELO Ranking System

* Trueskill system 이전에 체스 게임에 사용하기 위해 고안된 시스템</br>
* 각 player들의 실력이 정규 분포를 따른다고 가정하여 플레이더들의 실력 수준 확률 범위를 단순화 시킨 시스템 => 'pi ~ N (pi ; si ; β^2)'</br>
* 원리 
 1. player 1 이 이기면 y값은 1이 추가된다고 할 때, player 2가 이기면 y 값은 마이너스 1이 적용. 만약 무승부일경우, y는 0. </br>
 2. 즉, s1 ← s1 + yΔ ,  s2 ← s2 - yΔ. 
  
* 공식 </br>

<!-- 숫자를 이용하여 이해해보자면, 다음과 같이 예시를 들 수 있다. 
음, 간단히 말하자면 A:B 가 3:2일 때, A가 B를 이길 확률을 로그를 사용한 후 400을 곱하고 기준 점수를 더하여 계산하는 것이 Elo 점수이다. 
예를 들어, 기준 점수가 1000 점 일 때, 실력지수를 구하기 위한 Elo 점수 = 1000 + 400 log S , where 실력 지수 S = 400*logS.
이렇게 하는 이유 는 차이가 10배일 때, 400 점 차이나게 만든다  (최근에 사용되는 경우는 가우시안 대신 로그 distribution 을 사용한다.) 
 ELO System에는 "점수 차이가 400이 날 때, 실력 차이는 10배가 난다"는 가정이 삽입되어 있다. -->

![image](https://user-images.githubusercontent.com/61037197/130185178-9e656539-e5bf-4b6e-8549-927f974e30a0.png)

![image](https://user-images.githubusercontent.com/61037197/130185437-abdcf55f-5b4c-4704-bd24-f75fc08537b6.png)
(출처 : https://www.youtube.com/watch?v=VnOVLBbYlU0&t=774s)
* 가정 : 점수 차이가 400이 날 때, 실력 차이는 10배</br>
  -> A가 B를 이길 확률을 로그를 씌운 후, 400을 곱하고 기준 점수를 더하여 계산하는 것 </br>
  -> 예를 들어 기준 점수가 1000점이라 하자. Elo 점수는 1000 + 400log S 이다. 이 때, 실력 지수 S = 400 * logS
* K-factor은 신규 유저와 숙련된 유저에 따라 다르게 적용
* 실제 실력 측정을 위해 오랜 시간 필요


### :eye_speech_bubble: Trueskill Ranking System















:dragon: Trueskill 실습!

우선 trueskill library 설치!
```python
$ pip install trueskill

```
그 다음, trueskill import하여 사용하기 
```python
import trueskill 
```






😉 참고 
* https://brightwing1218.tistory.com/10
* https://www.youtube.com/watch?v=VnOVLBbYlU0&t=774s
* https://trueskill.org/
* https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/
* https://www.microsoft.com/en-us/research/publication/trueskilltm-a-bayesian-skill-rating-system/?from=http%3A%2F%2Fresearch.microsoft.com%2Fapps%2Fpubs%2Fdefault.aspx%3Fid%3D67956


