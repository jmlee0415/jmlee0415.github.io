---
title: "[Report - True Skill] "
date: 2021-03-02T21:31:46+09:00
draft: false
description: "TrueSkill 논문 읽기 "
tags: [REPORT]
categories: [REPORT]
toc : true
toc_sticky : true
toc_label : 목차
---
<참고 자료>
* 원 논문 : TrueSkillTM: A Bayesian Skill Rating System
    * https://www.microsoft.com/en-us/research/wp-content/uploads/2007/01/NIPS2006_0688.pdf

### <Abstract>


<Introduction>
 
  * Elo system에 대한 아이디어는 두 게임 플레이어들의 점수를 s1, s2로 지정. </br>
  이후 s1, s2를 함수에 이용하여 선수들의 게임 결과에 대한 확률을 모델링한 것.  
  * 정규 분포를 따름
    * 'i' 가 each player, 's' 는 skill and 'p' 는 performance 일 때,
      * ![image](https://user-images.githubusercontent.com/61037197/130378553-f72bc340-c5aa-45ca-af08-7bcfa5b873ac.png)
      *  위의 식은 player 1이 이기는 확률로, player 1의 performance p1이 상대방의 performance p2를 
        능가할 확률과 같다. 
  * 게임이 끝난 이후, s1 과 s2는 업데이트 되며, s1 + s2 는 상수 유지
  * player 1 이 이기면 y값은 1이 추가된다고 할 때, player 2가 이기면 y 값은 마이너스 1이 적용. </br>
    만약 무승부일경우, y는 0.
  * Elo 공식에 적용하는 업데이트는 : s1 ← s1 + yΔ , s2 ← s2 - yΔ 그리고
      ![image](https://user-images.githubusercontent.com/61037197/130378267-2e5f8afb-a11b-4ab8-922e-bfce7ca5d516.png)
  * 즉, s1 ← s1 + yΔ , s2 ← s2 - yΔ.
  * 여기서, 0 < α < 1로, 이전의 평가에 새로운 결과를 비교 후 측정 정도를 결정. ---> 수정
  * 최근에 사용되는 Elo variants는 가우시안 보단 logistic distribution을 사용 (체스 데이터에 더 적합하기 때문)
  * 따라서, ![image](https://user-images.githubusercontent.com/61037197/130383191-57ca7ead-5f12-4896-907d-5dc96cde88f3.png)

  * 문제점 : 
  
  
  
  
  
    ![image](https://user-images.githubusercontent.com/61037197/130378267-2e5f8afb-a11b-4ab8-922e-bfce7ca5d516.png)

  ![image](https://user-images.githubusercontent.com/61037197/130378288-f224d84b-b175-4c05-86a5-406f0cc5883d.png)
    
 skill rating은 
  
  
  
  
Reference 
* 논문 쓰는 방법 : https://dos-tacos.github.io/paper%20review/xdeepfm/
* https://web.stanford.edu/class/stats200/Lecture20.pdf
* http://norman3.github.io/prml/docs/chapter08/0.html












