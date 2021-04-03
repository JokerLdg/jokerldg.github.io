---
layout: post
title: 프로그래머스 3진법 뒤집기 (python 파이썬)
subtitle: 프로그래머스 3진법 뒤집기
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 3진법 뒤집기 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 3진법 뒤집기 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/68935){:target="_blank"}

### 문제 
자연수 n이 매개변수로 주어집니다. n을 3진법 상에서 앞뒤로 뒤집은 후, 이를 다시 10진법으로 표현한 수를 return 하도록 solution 함수를 완성해주세요.

### 제한사항
* n은 1 이상 100,000,000 이하인 자연수입니다.

### 입출력 예

|n|lost|
|-----|-----|
|45|7|
|125|229|

### 입출력 예 설명
**예제 #1**  
* 답을 도출하는 과정은 다음과 같습니다.

|n (10 진법)|n (3진법)|앞뒤 반전(3진법)|10진법으로 표현|
|------------|------------|-----------|-----------|
|45|1200|0021|7|

* 따라서 7을 return 해야 합니다.

**예제 #2**  
* 답을 도출하는 과정은 다음과 같습니다.

|n (10 진법)|n (3진법)|앞뒤 반전(3진법)|10진법으로 표현|
|------------|------------|-----------|-----------|
|125|11122|22111|229|

* 따라서 229을 return 해야 합니다.


### 문제풀이
* 삼진법을 먼저 거꾸로 만들기 위해 n을 3으로 나눈 나머지 값을 저장해준다.
* 배열의 맨 뒤에서부터 제곱근 계산을 해주어 값을 더해준다.

### 코드
```python
import math

def solution(n):
    answer = 0
    three = []

    while n != 0:
      three.append(n%3)
      n //= 3

    for i in range(len(three)-1, -1, -1):
      answer += three[i] * math.pow(3,(len(three)-1) - i)

    return answer
```