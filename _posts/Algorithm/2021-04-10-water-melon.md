---
layout: post
title: 프로그래머스 수박수박수박수박수박수? (python 파이썬)
subtitle: 프로그래머스 수박수박수박수박수박수?
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 수박수박수박수박수박수? 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 수박수박수박수박수박수? 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12922){:target="_blank"}

### 문제 
길이가 n이고, "수박수박수박수...."와 같은 패턴을 유지하는 문자열을 리턴하는 함수, solution을 완성하세요. 예를들어 n이 4이면 "수박수박"을 리턴하고 3이라면 "수박수"를 리턴하면 됩니다.

### 제한사항
* n은 길이 10,000이하인 자연수입니다.

### 입출력 예

|n|return|
|-----|-----|
|3|"수박수"|
|4|"수박수박"|

### 문제풀이
* 2로 나누었을때 0이면 수, 아니면 박을 문자열에 더해주면 된다.

### 코드
```python
def solution(n):
    answer = ''

    for i in range(n):
        if (i % 2) == 0:
            answer += '수'
        else:
            answer += '박'

    return answer
```
