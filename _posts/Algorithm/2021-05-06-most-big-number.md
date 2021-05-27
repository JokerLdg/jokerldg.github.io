---
layout: post
title: 프로그래머스 가장 큰 수 (python 파이썬)
subtitle: 프로그래머스 가장 큰 수
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 가장 큰 수 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 가장 큰 수 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/42746){:target="_blank"}


### 문제 설명
0 또는 양의 정수가 주어졌을 때, 정수를 이어 붙여 만들 수 있는 가장 큰 수를 알아내 주세요.

예를 들어, 주어진 정수가 [6, 10, 2]라면 [6102, 6210, 1062, 1026, 2610, 2106]를 만들 수 있고, 이중 가장 큰 수는 6210입니다.

0 또는 양의 정수가 담긴 배열 numbers가 매개변수로 주어질 때, 순서를 재배치하여 만들 수 있는 가장 큰 수를 문자열로 바꾸어 return 하도록 solution 함수를 작성해주세요.


### 제한사항
* numbers의 길이는 1 이상 100,000 이하입니다.
* numbers의 원소는 0 이상 1,000 이하입니다.
* 정답이 너무 클 수 있으니 문자열로 바꾸어 return 합니다.


### 입출력 예

|numbers|return|
|-----|-----|
|[6, 10, 2]|"6210"|
|[3, 30, 34, 5, 9]|"9534330"|


### 문제풀이
* int형의 list를 map을 사용하여 string으로 치환한 뒤, list로 변환한다.
* 변환된 num을 sort()를 사용하여 key 조건에 맞게 정렬한다.  
lambda x : x * 3은 num 인자 각각의 문자열을 3번 반복한다는 뜻이다. 
    * **x * 3을 하는 이유?**
        * num의 인수값이 1000 이하이므로 3자리수로 맞춘 뒤, 비교하겠다는 뜻.
* 문자열 비교는 ASCII 값으로 치환되어 정렬된다. 따라서 666, 101010, 222의 첫번째 인덱스 값으로 비교한다. 
    * 6 = 86, 1 = 81, 2 = 82 이므로 6 > 2 > 1순으로 크다. 
    * sort()의 기본 정렬 기준은 오름차순이다. reverse = True 전의 sort된 결과값은 10, 2, 6이다. 
    * 이를 reverse = True를 통해 내림차순 해주면 6,2,10이 된다. 이것을 ''.join(num)을 통해 문자열을 합쳐주면 된다. 
    * **int로 변환한 뒤, 또 str로 변환해주는 이유?**  
        * 모든 값이 0일 때(즉, '000'을 처리하기 위해) int로 변환한 뒤, 다시 str로 변환한다. 

### 코드
```python
def solution(numbers):
    numbers = list(map(str, numbers))
    numbers.sort(key=lambda x: x * 3, reverse=True)
    return str(int(''.join(numbers)))
```