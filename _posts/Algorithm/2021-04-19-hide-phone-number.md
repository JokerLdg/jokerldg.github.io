---
layout: post
title: 프로그래머스 핸드폰 번호 가리기 (python 파이썬)
subtitle: 프로그래머스 핸드폰 번호 가리기
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 핸드폰 번호 가리기 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 핸드폰 번호 가리기 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12948){:target="_blank"}

### 문제 
프로그래머스 모바일은 개인정보 보호를 위해 고지서를 보낼 때 고객들의 전화번호의 일부를 가립니다.
전화번호가 문자열 phone_number로 주어졌을 때, 전화번호의 뒷 4자리를 제외한 나머지 숫자를 전부 *으로 가린 문자열을 리턴하는 함수, solution을 완성해주세요.


### 제한사항
* s는 길이 4 이상, 20이하인 문자열입니다.

### 입출력 예

|phone_number|return|
|-----|-----|
|"01033334444"|"*******4444"|
|"027778888"|"*****8888"|


### 문제풀이
* 파이썬의 * 기능을 이용하여 핸드폰 번호의 길이 -4만큼 곱해주고, 배열의 뒤에서 4번째 부터 마지막 길이까지 더해준다.

### 코드
```python
def solution(phone_number):
    return "*"*(len(phone_number)-4) + phone_number[-4:]
```
