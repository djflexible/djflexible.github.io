---
layout: blog
title:  "알고리즘 - 컴퓨터 알고리즘 기초2"
date:   2016-05-21
categories: blog
---
목표

- 컴퓨터 알고리즘의 4단계 이해하기
- 컴퓨터 알고리즘의 성능분석 이해하기
- 성능 분석을 위한 점근적 표기법인 빅-오(Big-Oh), 오메가(Omega), 세타(Theta) 이해하기

# 1.1. 컴퓨터 알고리즘의 분석 4단계

- 문제 정의
- 알고리즘 설명
- 정확성 증명
- 성능 분석

# 1.2.1. 컴퓨터 알고리즘의 수행시간 분석

- 수행연산의 횟수를 비교하는 방식으로 성능을 분석
- 수행하는데 걸리는 전체적인 시간이 아님
- 몇 번의 연산을 수행해서 얼마의 시간이 걸리는가?
- 입력의 크기가 클수록 시간이 많이 걸림(ex 같은 자료를 10개의 key로 정렬하는 시간이 100개의 key로 정렬하는 시간보다 길다)
- 수행시간은 입력 크기 n에 대한 함수로 표현(ex T(n), n에 대한 다항식에서 최고차 항만을 고려)

# 1.2.2. 성능 분석의 비교 대상

산술 연산(Arithmetic Calculation)

- add, multiply, exponent, modular 등

데이터 입출력(Data Movement)

- copy, move, save, load 등

제어 연산(Access Control)

- if, while, register 등

# 2. 점근적 표기법(Asymptotic notation)

- 빅-오(Big-Oh) 표기
- 오메가(Omega) 표기
- 세타(Theta) 표기

# 2.1 빅-오(Big-Oh) 표기

![oh](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/algorithm/algorithm-big-oh.png)

변수 설명

- cg(n) : 기준 함수
- f(n) : 평가하려는 함수
- 세로 : 시간
- 가로 : 횟수

f(n)이 아무리 느려진다 하더라도 주어진 상한 g(n)보다는 빠르다.

# 2.2. 오메가(Omega) 표기

![omega](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/algorithm/algorithm-omega.png)

변수 설명

- cg(n) : 기준 함수
- f(n) : 평가하려는 함수
- 세로 : 시간
- 가로 : 횟수

f(n)이 아무리 빨라진다 하더라도 주어진 하한 g(n)보다는 느리다.

# 2.3. 세타(Theta) 표기

![theta](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/algorithm/algorithm-theta.png)

변수 설명

- cg(n) : 기준 함수
- f(n) : 평가하려는 함수
- 세로 : 시간
- 가로 : 횟수

빅오&오메가를 함께 씀, f(n)이 g(n1), g(n2) 영역에 있다.




참고문헌


[T아카데미 조호성][T아카데미 조호성]님

[T아카데미 조호성]: https://tacademy.sktechx.com/live/player/listOnline.action#

update : 2016-05-21