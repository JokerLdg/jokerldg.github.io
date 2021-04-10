---
layout: post
title: 프로그래머스 문자열을 정수로 바꾸기 (python 파이썬)
subtitle: 프로그래머스 문자열을 정수로 바꾸기
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 문자열을 정수로 바꾸기 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 문자열을 정수로 바꾸기 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12925){:target="_blank"}

### 문제 
문자열 s를 숫자로 변환한 결과를 반환하는 함수, solution을 완성하세요.

### 제한사항
* s의 길이는 1 이상 5이하입니다.
* s의 맨앞에는 부호(+, -)가 올 수 있습니다.
* s는 부호와 숫자로만 이루어져있습니다.
* s는 "0"으로 시작하지 않습니다.

### 입출력 예
예를들어 str이 "1234"이면 1234를 반환하고, "-1234"이면 -1234를 반환하면 됩니다.  
str은 부호(+,-)와 숫자로만 구성되어 있고, 잘못된 값이 입력되는 경우는 없습니다.

### 문제풀이
* 문제를 2가지 방식으로 풀어보았다.
* 1번 풀이
    * 파이썬의 int함수를 이용하여 그냥 정수형으로 바꿔서 리턴하는방법이다.
* 2번 풀이
    * s[::-1]은 주어진 스트링을 거꾸로 만든다.
    * enumerate 함수를 이용하여 한 글자당 인덱스를 배정해서 각 자리에 10의 지수만큼 곱해서 더해준다.
    * 예를들면 -1234는 s[::-1]에 의해 "4321-"가 되고 
    1. 4 * (10 ** 0) : 4
    2. 3 * (10 ** 1) : 30
    3. 2 * (10 ** 2) : 200
    4. 1 * (10 ** 3) : 1000
    5. "-" : result * -1
    6. 1~5까지 항목을 하면 1000+200+30+4 = 1234 * -1 이므로 -1234의 결과값이 나온다.


### 코드1
```python
def solution(s):
    return int(s)
```

### 코드2
```python
def solution(s):
    result = 0

    for idx, number in enumerate(s[::-1]):
        if number == '-':
            result *= -1
        else:
            result += int(number) * (10 ** idx)

    return result
```