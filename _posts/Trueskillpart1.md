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

:octocat:

### :octocat: Trueskill 이란..?

Trueskill system은 간단히 말해 마이크로소프트가 출시한 '멀티플레이어 랭킹 시스템'이다! 
Tureskill systmem의 이해를 돕기 위해 우선 ELO 랭킹 시스템을 먼저 알아볼 필요가 있다. 


#### :eyes: ELO Ranking System

ELO 랭킹 시스템은 Trueskill system 이전에 먼저 고안되었다. 
각 player들의 실력이 정규 분포를 따른다고 가정하여 플레이더들의 실력 수준 확률 범위를 단순화 시킨 시스템이다. => 'pi ~ N (pi ; si ; β^2)'
이는 체스 게임을 염두하여 고안된 시스템이기 때문이다. 
시스템의 기본 원리는 다음과 같다. 
player 1 이 이기면 y값은 1이 추가된다고 할 때, player 2가 이기면 y 값은 마이너스 1이 적용된다. 만약 무승부일경우, y는 0이다. 
즉, s1 ← s1 + yΔ , s2 ← s2 - yΔ 시스템이다. 

숫자를 이용하여 이해해보자면, 다음과 같이 예시를 들 수 있다. 
음, 간단히 말하자면 A:B 가 3:2일 때, A가 B를 이길 확률을 로그를 사용한 후 400을 곱하고 기준 점수를 더하여 계산하는 것이 Elo 점수이다. 
예를 들어, 기준 점수가 1000 점 일 때, 실력지수를 구하기 위한 Elo 점수 = 1000 + 400 log S , where 실력 지수 S = 400*logS.
이렇게 하는 이유 는 차이가 10배일 때, 400 점 차이나게 만든다  (최근에 사용되는 경우는 가우시안 대신 로그 distribution 을 사용한다.) 
 ELO System에는 "점수 차이가 400이 날 때, 실력 차이는 10배가 난다"는 가정이 삽입되어 있다.
다음은 ELO 랭킹 시스템에서 이용한 공식이다. 

```
RatingDiff = (Score - Expected) * K-factor, 
where
Score is 0 = loss, 0.5 = draw, 1 = win 
Expected is 0 to 1, the porbability of winning
K-factor is a constant for maximum change (update "speed")
```

이 때, K-factor은 신규 유저와 숙련된 유저에 따라 다르게 적용된다. 










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


