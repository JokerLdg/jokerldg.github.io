---
layout: post
title: 프로그래머스 이상한 문자 만들기 (python 파이썬)
subtitle: 프로그래머스 이상한 문자 만들기
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 이상한 문자 만들기 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 이상한 문자 만들기 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12930){:target="_blank"}

### 문제 
문자열 s는 한 개 이상의 단어로 구성되어 있습니다. 각 단어는 하나 이상의 공백문자로 구분되어 있습니다. 각 단어의 짝수번째 알파벳은 대문자로, 홀수번째 알파벳은 소문자로 바꾼 문자열을 리턴하는 함수, solution을 완성하세요.

### 제한사항
* 문자열 전체의 짝/홀수 인덱스가 아니라, 단어(공백을 기준)별로 짝/홀수 인덱스를 판단해야합니다.
* 첫 번째 글자는 0번째 인덱스로 보아 짝수번째 알파벳으로 처리해야 합니다.  


### 입출력 예

|s|return|
|-----|-----|
|"try hello world"|"TrY HeLlO WoRlD"|

### 입출력 예 설명
"try hello world"는 세 단어 "try", "hello", "world"로 구성되어 있습니다. 각 단어의 짝수번째 문자를 대문자로, 홀수번째 문자를 소문자로 바꾸면 "TrY", "HeLlO", "WoRlD"입니다. 따라서 "TrY HeLlO WoRlD" 를 리턴합니다.

### 문제풀이
1. 공백을 기준으로 문자를 나눠준다.
2. 그리고 글자 인덱스에 맞게 2로 나눈경우 나머지가 0이면 대문자로, 아니면 소문자로 변경한다.

### 코드
```python
def solution(s):
    answer = []
    s = s.split(' ')

    for i in range(len(s)):
        result = ''
        for j in range(len(s[i])):
            if j % 2 == 0:
                result += s[i][j].upper()
            else:
                result += s[i][j].lower()

        answer.append(result)

    return ' '.join(answer)
```
