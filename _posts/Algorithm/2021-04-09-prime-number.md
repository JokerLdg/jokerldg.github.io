---
layout: post
title: 프로그래머스 소수 찾기 (python 파이썬)
subtitle: 프로그래머스 소수 찾기
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 소수 찾기 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 소수 찾기 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12921){:target="_blank"}

### 문제 
1부터 입력받은 숫자 n 사이에 있는 소수의 개수를 반환하는 함수, solution을 만들어 보세요.

소수는 1과 자기 자신으로만 나누어지는 수를 의미합니다.
(1은 소수가 아닙니다.)

### 제한사항
* n은 2이상 1000000이하의 자연수입니다.

### 입출력 예

|n|result|
|-----|-----|
|10|4|
|5|3|

### 입출력 예 설명
**예제 #1**  
1부터 10 사이의 소수는 [2,3,5,7] 4개가 존재하므로 4를 반환

**예제 #2**  
1부터 5 사이의 소수는 [2,3,5] 3개가 존재하므로 3를 반환

### 문제풀이
* 에라토스테네스의 체를 이용하여 소수를 찾는다.
* 에라토스테네스의 체
	1. 2부터 n까지의 숫자를 배열로 만든다.
	2. 2를 제외하고 2의배수를 만든 배열에서 제거한다.
	3. 1씩 커지면서 그숫자의 배수를 제거한다.


### 코드
```python
def solution(n):
	# 2부터 n까지의 숫자 배열 만들기
    num_set = set(range(2, n+1))

    for i in range(2, n+1):
        if i in num_set: # 배수 제거
            num_set -= set(range(i*2, n+1, i))

    answer = len(num_set)

    return answer
```
