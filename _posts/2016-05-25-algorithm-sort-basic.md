---
layout: blog
title:  "알고리즘 - 정렬(sort)의 개념"
date:   2016-05-25
categories: blog
---
목표
- 컴퓨터 알고리즘의 정렬의 개념에 대해 알아본다.

# 1. 정렬의 개념

- 순서 없이 배열되어 있는 자료들을 오름차순(ascending) 혹은 내림차순(descending)으로 재배열하는 것이다.
- 자료를 정렬하는 데 사용하는 기준이 되는 특정 값을 key라고 한다.

# 2. 정렬 방법의 분류

정렬은 다음과 같이 분류될 수 있다.

- 정렬을 실행하는 방법
- 정렬이 수행되는 장소

# 2.1. 정렬의 실행 방법에 따른 분류

- 비교식 정렬(Comparative Sort) : 비교하고자 하는 각 키 값들을 한 번에 두 개씩 비교하여 교환하는 방식으로 정렬을 실행 ex) 선택정렬, 삽입정렬, 퀵 정렬 버블 정렬 등

- 분산식 정렬(Distribute Sort) : 키 값을 기준으로, 자료를 여러 개의 부분집합으로 분해하고, 각 부분집합을 정렬함으로써 전체를 정렬하는 방식으로 실행한다. ex) 하둡 분산처리 시스템

# 2.2. 정렬 장소에 따른 분류

# 2.2.1. 내부 정렬(Internal Sort)

- 컴퓨터 메모리 내부에서 정렬
- 메모리에 올려서 정렬하기 때문에 속도가 빠르다.
- 정렬할 수 있는 자료의 양이 메인 메모리의 용량에 따라 제한된다.
- 정렬하는 방식에 따라 다음과 같이 분류

정렬하는 방식에 따라 다음과 같이 분류한다.

- 교환 방식 : 키를 비교하고 교환하여 정렬하는 방식 ex) 선택, 버블, 퀵 정렬
- 삽입 방식 : 키를 비료하고 삽입하여 정렬하는 방식 ex) 삽입, 셸 정렬
- 병합 방식 : 키를 비료하고 병합하여 정렬하는 방식 ex) 2-way 병합, n-way 병합
- 분배 방식 : 키를 구성하는 값을 여러 개의 부분집합에 분배하여 정렬하는 방식 ex) 기수 정렬
- 선택 방식 : 이진 트리를 사용하여 정렬하는 방식 ex) 힙, 트리 정렬

# 2.2.2. 외부 정렬(External Sort)

- 메모리의 외부인 보조 기억 장치에서 정렬
- 보조 기억 장치를 사용하기 때문에 내부 정렬보다 속도가 떨어진다.
- 내부 정렬로 처리할 수 없는 대용량의 자료를 처리할 수 있다.
- 병합 방식 : 파일을 부분 파일로 분리한 후 각각을 내부 정렬 방법으로 정렬하여 병합하는 정렬 방식 ex) 병합 방식(2-way병합, n-way 병합), 테이프를 이용한 균형 병합 정렬, 계단식 병합 정렬, 다단계 병합 정렬, 교대식 병합 정렬

병합 정렬의 예를 보여주는 그림

![external](https://s3-ap-northeast-1.amazonaws.com/dongjoo/poster/algorithm/external-sort.png)



참고문헌

[위키백과][위키백과], [stackExchange][stackExchange], [sw-tech][sw-tech]님,  책 - '자바로 배우는 쉬운 자료구조'

[위키백과]: https://en.wikipedia.org/wiki/Comparison_sort
[stackExchange]: http://cs.stackexchange.com/questions/49504/how-to-understand-the-storing-mechanism-used-in-external-merge-sort
[sw-tech]: http://sw-tech.tistory.com/entry/%EC%A0%95%EB%A0%AC%EC%99%B8%EB%B6%80%EC%A0%95%EB%A0%AC

update : 2016-05-25