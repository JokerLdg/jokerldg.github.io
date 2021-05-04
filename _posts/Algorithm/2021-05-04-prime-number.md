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

* [프로그래머스 소수 찾기 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/42839){:target="_blank"}


### 문제 
한자리 숫자가 적힌 종이 조각이 흩어져있습니다. 흩어진 종이 조각을 붙여 소수를 몇 개 만들 수 있는지 알아내려 합니다.

각 종이 조각에 적힌 숫자가 적힌 문자열 numbers가 주어졌을 때, 종이 조각으로 만들 수 있는 소수가 몇 개인지 return 하도록 solution 함수를 완성해주세요.


### 제한사항
* numbers는 길이 1 이상 7 이하인 문자열입니다.
* numbers는 0~9까지 숫자만으로 이루어져 있습니다.
* "013"은 0, 1, 3 숫자가 적힌 종이 조각이 흩어져있다는 의미입니다.


### 입출력 예

|numbers|return|
|-----|-----|
|"17"|3|
|"011"|2|

### 입출력 예 설명
**예제 #1**  
[1, 7]으로는 소수 [7, 17, 71]를 만들 수 있습니다.

**예제 #2**  
[0, 1, 1]으로는 소수 [11, 101]를 만들 수 있습니다.
* 11과 011은 같은 숫자로 취급합니다.

### 문제풀이
* 파이썬의 permutations을 이용하여 자릿수만큼 숫자를 list로 만든다.
* 만든 숫자를 check함수를 이용하여 각 숫자를 소수인지 아닌지 판단한다.
    * 소수 판단방법은 판단할 숫자의 제곱근을 구한다.
    * 2보다 작으면 소수가 아니므로 False
    * 2이상이면 2부터 제곱근만큼 반복문을 실행하는데, 그 값으로 나누어 떨어지면 소수가 아니다.

### 코드
```python
from itertools import permutations
import math

def check(n):
    k = math.sqrt(n)
    if n < 2: 
        return False

    for i in range(2, int(k)+1):
        if n % i == 0:
            return False
    return True

def solution(numbers):
    answer = []
    for k in range(1, len(numbers)+1):
        per_list = list(map(''.join, permutations(list(numbers), k)))
        for i in list(set(per_list)):
            if check(int(i)):
                answer.append(int(i))

    answer = len(set(answer))

    return answer
```
