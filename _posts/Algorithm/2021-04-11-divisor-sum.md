---
layout: post
title: 프로그래머스 약수의 합 (python 파이썬)
subtitle: 프로그래머스 약수의 합
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 약수의 합 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 약수의 합 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12928){:target="_blank"}

### 문제 
정수 n을 입력받아 n의 약수를 모두 더한 값을 리턴하는 함수, solution을 완성해주세요.

### 제한사항
* n은 0 이상 3000이하인 정수입니다.

### 입출력 예

|n|return|
|-----|-----|
|12|28|
|5|6|

### 문제풀이
* 먼저 합에 n값을 넣은후에 n//2의 값만큼 돌면서 n % i가 0인경우 합에 더해주면 된다.

### 코드
```python
def solution(n):
    answer = n

    for i in range(1, (n//2) + 1):
        if n % i == 0:
            answer += i

    return answer
```
