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
  -> 예를 들어, 기준 점수가 1000점이라 하자. Elo 점수는 1000 + 400log S 이다. 이 때, 실력 지수 S = 400 * logS
* K-factor은 신규 유저와 숙련된 유저에 따라 다르게 적용
* 실제 실력 측정을 위해 오랜 시간 필요


### :eye_speech_bubble: Trueskill Ranking System

* Microsoft Research가 고안
* 가우시안 분포를 따르며, 각 팀의 실력은 팀플레이어들의 실력의 합이라 가정
* 두 변수를 이용 : μ (평균 실력) & σ (불확실성 정도) => 불확실성이 작아질수록 플레이어의 기술이 평균 실력에 가깝다. 
* 
<!-- 이 모형은 각 선수의 시간에 따라 서서히 변하는 skill 값 s가 평균 mu, 표준편차 sigma의 정규 분포를 따른다고(베이지안 추론에서의 사전분포) 가정하고 선수가 각 경기에서 보여주는 performance p 는 평균이 s, 표준편차가 beta(권장되는 값은 (초기 sigma)/2. 이 블로그에서는 1000/2 = 500.)인 정규 분포를 따른다고 가정한다.
매 트랙마다 우리가 관측하는 것은 개인전의 경우 각 선수의 performance p의 순위, 팀전의 경우 각 팀의 p의 합이 어느 쪽이 큰 지이다. 랭킹 모형은 이 관측된 값을 토대로 approximate message passing이라는 방법을 통해 s의 사후 분포(경기 결과가 주어졌을 때의 s의 분포)를 계산한다. 계산된 사후 분포는 사전 분포와 마찬가지로 평균 mu’, 표준편차 sigma’를 따르는 정규 분포로 나타나고, 이 사후 분포를 이후 트랙에서 각 선수의 skill에 대한 사전 분포로 사용하게 되어 mu와 sigma를 점진적으로 업데이트해나가게 된다. (조금 더 정확하게는 시간에 따른 skill의 변화를 원활하게 추정하기 위해 다음 사전 분포의 분산을 약간 더 키워 주는 추가적인 파라미터 tau가 사용된다.)

이 블로그의 모든 모형에는 다음 파라미터가 사용된다: 초기 mu = 3000, 초기 sigma = 1000, beta = 500, tau = 10. -->

![image](https://user-images.githubusercontent.com/61037197/130193216-cb073530-26e7-497b-a403-4a855711f670.png)
(출처 : https://www.youtube.com/watch?v=VnOVLBbYlU0&t=774s)

* 여러 종류의 게임에 적용할 수 있음 ( 1:1, 팀:팀)
* 계산이 복잡 -> 컴퓨터는 이해할 수 있지만, 플레이어들은 혼란스러울 수 있음
* 실제 실력을 몇 게임만으로도 측정할 수 있음
* 신규 플레이어의 실력 측정이 쉬움 



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
* https://kartranking.github.io/about/
* http://koreascience.kr/article/JAKO202007650437365.pdf
* https://kartranking.github.io/power-ranking-20210515/ 랭킹 스피드전 참고
