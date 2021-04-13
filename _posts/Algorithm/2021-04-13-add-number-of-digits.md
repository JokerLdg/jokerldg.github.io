---
layout: post
title: 프로그래머스 자릿수 더하기 (python 파이썬)
subtitle: 프로그래머스 자릿수 더하기
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 자릿수 더하기 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 자릿수 더하기 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12931){:target="_blank"}

### 문제 
자연수 N이 주어지면, N의 각 자릿수의 합을 구해서 return 하는 solution 함수를 만들어 주세요.
예를들어 N = 123이면 1 + 2 + 3 = 6을 return 하면 됩니다.

### 제한사항
* N의 범위 : 100,000,000 이하의 자연수


### 입출력 예

|N|answer|
|-----|-----|
|123|6|
|987|24|

### 입출력 예 설명
**예제 #1**  
문제의 예시와 같습니다.

**예제 #2**  
9 + 8 + 7 = 24이므로 24를 return 하면 됩니다.

### 문제풀이
* 파이썬의 str을 이용하여 각 자릿수별로 더하면 된다.

### 코드
```python
def solution(n):
    answer = 0

    for num in str(n):
        answer += int(num)

    return answer
```
