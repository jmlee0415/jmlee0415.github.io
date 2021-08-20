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



:crocodile: TrueSkill 이란..?

간단히 말하면 마이크로소프트가 출시한 '멀티플레이어 랭킹 시스템'이다! 
사실, Trueskill 시스템 이전에 ELO 랭킹 시스템이 존재했다. 
ELO 랭킹 시스템은 각 player들의 실력이 정규 분포를 따른 다고 가정하여 플레이어들의 실력 수준 확률 범위를 단순화 시켰다. 그러나 이는 1 vs 1 게임 상황을 가정한 것이다. 

다음은 ELO 랭킹 시스템에서 이용한 공식이다. 

```
RatingDiff = (Score - Expected) * K-factor, 
where
Score is 0 = loss, 0.5 = draw, 1 = win 
Expected is 0 to 1, the porbability of winning
K-factor is a constant for maximum change (update "speed")
```

음, 간단히 말하자면 A:B 가 3:2일 때, A가 B를 이길 확률을 로그를 사용한 후 400을 곱하고 기준 점수를 더하여 계산하는 것이 Elo 점수이다. 
예를 들어, 기준 점수가 1000 점 일 때, 실력지수를 구하기 위한 Elo 점수 = 1000 + 400 log S , where 실력 지수 S = 400*logS.
이렇게 하는 이유 는 차이가 10배일 때, 400 점 차이나게 만든다



Trueskill을 이해하기 위해 ELO 랭킹 시스템을 간단히 알아볼 필요가 있다. 

ELO 랭킹 시스템은 TrueSkill 시스템이 나오기 이전에 출시된 것으로, 각 player들의 실력이 정규 분포를 따른다고 가정한다. 









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
* https://trueskill.org/
* https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/
* https://www.microsoft.com/en-us/research/publication/trueskilltm-a-bayesian-skill-rating-system/?from=http%3A%2F%2Fresearch.microsoft.com%2Fapps%2Fpubs%2Fdefault.aspx%3Fid%3D67956


