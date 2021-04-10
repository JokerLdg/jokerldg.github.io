---
layout: post
title: 프로그래머스 시저 암호 (python 파이썬)
subtitle: 프로그래머스 시저 암호
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 시저 암호 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 시저 암호 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12926){:target="_blank"}

### 문제 
어떤 문장의 각 알파벳을 일정한 거리만큼 밀어서 다른 알파벳으로 바꾸는 암호화 방식을 시저 암호라고 합니다.  

예를 들어 "AB"는 1만큼 밀면 "BC"가 되고, 3만큼 밀면 "DE"가 됩니다. "z"는 1만큼 밀면 "a"가 됩니다. 문자열 s와 거리 n을 입력받아 s를 n만큼 민 암호문을 만드는 함수, solution을 완성해 보세요.

### 제한사항
* 공백은 아무리 밀어도 공백입니다.
* s는 알파벳 소문자, 대문자, 공백으로만 이루어져 있습니다.
* s의 길이는 8000이하입니다.
* n은 1 이상, 25이하인 자연수입니다.

### 입출력 예

|s|n|result|
|-----|-----|-----|
|"AB"|1|"BC"|
|"z"|1|"a"|
|"a B z"|4|"e F d"|

### 문제풀이
* 문자가 대문자인경우 아스키코드로 바꾼후 대문자 A의 아스키코드 값을 뺀후 n을 더하고 26의 나머지값에 다시 대문자 A의 아스키코드 값을 더한다.
* 문자가 소문자인경우 아스키코드로 바꾼후 소문자 a의 아스키코드 값을 뺀후 n을 더하고 26의 나머지값에 다시 소문자 a의 아스키코드 값을 더한다.
* 그게 아닌경우 공백이므로 공백을 더해준다.

### 코드
```python
def solution(s, n):
    answer = ''

    for word in s:
        if word.isupper():
            answer += chr((ord(word) - ord('A') + n) % 26 + ord('A'))
        elif word.islower():
            answer += chr((ord(word) - ord('a') + n) % 26 + ord('a'))
        else:
            answer += word

    return answer
```
