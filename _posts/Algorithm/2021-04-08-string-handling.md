---
layout: post
title: 프로그래머스 문자열 다루기 기본 (python 파이썬)
subtitle: 프로그래머스 문자열 다루기 기본
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 문자열 다루기 기본 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 문자열 다루기 기본 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12918){:target="_blank"}

### 문제 
문자열 s의 길이가 4 혹은 6이고, 숫자로만 구성돼있는지 확인해주는 함수, solution을 완성하세요. 예를 들어 s가 "a234"이면 False를 리턴하고 "1234"라면 True를 리턴하면 됩니다.

### 제한사항
* s는 길이 1 이상, 길이 8이하인 문자열입니다.

### 입출력 예

|s|return|
|-----|-----|
|"a234"|false|
|"1234"|true|

### 문제풀이
* 길이가 4나 6인지 비교후 isdigit함수를 이용하여 숫자를 판단한다

### 코드
```python
def solution(s):
    answer = True
    
    if len(s) == 4 or len(s) == 6:
        if s.isdigit() == False:
            answer = False
    else:
        answer = False
    
    return answer
```
