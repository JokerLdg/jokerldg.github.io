---
layout: post
title: 프로그래머스 직사각형 별찍기 (python 파이썬)
subtitle: 프로그래머스 직사각형 별찍기
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 직사각형 별찍기 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 직사각형 별찍기 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12969){:target="_blank"}


### 문제 
이 문제에는 표준 입력으로 두 개의 정수 n과 m이 주어집니다.
별( * ) 문자를 이용해 가로의 길이가 n, 세로의 길이가 m인 직사각형 형태를 출력해보세요.

### 제한사항
* n과 m은 각각 1000 이하인 자연수입니다.

### 입출력 예  
#### 입력
```
5 3
```

#### 출력
```
*****
*****
*****
```

### 문제풀이
* b의 길이만큼 for문을 돌려서 파이썬의 * 연산을 이용하여 a를 출력해준다.

### 코드
```python
a, b = map(int, input().strip().split(' '))

for i in range(b):
    print('*' * a)
```
