---
layout: post
title: 프로그래머스 문자열 내림차순으로 배치하기 (python 파이썬)
subtitle: 프로그래머스 문자열 내림차순으로 배치하기
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 문자열 내림차순으로 배치하기 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 문자열 내림차순으로 배치하기 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12917){:target="_blank"}

### 문제 
문자열 s에 나타나는 문자를 큰것부터 작은 순으로 정렬해 새로운 문자열을 리턴하는 함수, solution을 완성해주세요.  
s는 영문 대소문자로만 구성되어 있으며, 대문자는 소문자보다 작은 것으로 간주합니다.

### 제한사항
* str은 길이 1 이상인 문자열입니다.

### 입출력 예

|s|answer|
|-----|-----|
|"Zbcdefg"|"gfedcbZ"|

### 문제풀이
* heapq를 이용하여 가장작은 숫자(음수)로 넣은후 작은것부터 빼면 내림차순으로 정렬된다.
* 다른 하나는 문자를 배열로 만든후 정렬하면 된다.

### 코드1
```python
import heapq

def solution(s):
  answer = ''
  queue = []

  for word in s:
    heapq.heappush(queue, -ord(word))
  
  for _ in range(len(queue)):
    answer += chr(-heapq.heappop(queue))

  return answer
```

### 코드2
```python
def solution(s):
  return ''.join(sorted(s, reverse=True))
```