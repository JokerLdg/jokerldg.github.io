---
layout: post
title: 프로그래머스 짝수와 홀수 (python 파이썬)
subtitle: 프로그래머스 짝수와 홀수
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 짝수와 홀수 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 짝수와 홀수 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12937){:target="_blank"}

### 문제 
정수 num이 짝수일 경우 "Even"을 반환하고 홀수인 경우 "Odd"를 반환하는 함수, solution을 완성해주세요.

### 제한사항
* num은 int 범위의 정수입니다.
* 0은 짝수입니다.

### 입출력 예

|num|return|
|-----|-----|
|3|"Odd"|
|4|"Even"|


### 문제풀이
* 2로 나눈 나머지가 0이면 Even, 아니면 Odd를 출력해준다.

### 코드
```python
def solution(num):
    answer = ''
    
    if (num % 2) == 0:
        answer = "Even"
    else:
        answer = "Odd"
    
    return answer
```
