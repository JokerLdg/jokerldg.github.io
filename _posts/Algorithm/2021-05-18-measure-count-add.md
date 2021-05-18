---
layout: post
title: 프로그래머스 약수의 개수와 덧셈 (python 파이썬)
subtitle: 프로그래머스 약수의 개수와 덧셈
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 약수의 개수와 덧셈 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 약수의 개수와 덧셈 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/77884){:target="_blank"}


### 문제 설명
두 정수 ```left```와 ```right```가 매개변수로 주어집니다. ```left```부터 ```right```까지의 모든 수들 중에서, 약수의 개수가 짝수인 수는 더하고, 약수의 개수가 홀수인 수는 뺀 수를 return 하도록 solution 함수를 완성해주세요.


### 제한 사항
* 1 ≤ ```left``` ≤ ```right``` ≤ 1,000


### 입출력 예

|left|right|result|
|-----|-----|-----|
|13|17|43|
|24|27|52|


### 입출력 예 설명
**예제 #1**  
* 다음 표는 13부터 17까지의 수들의 약수를 모두 나타낸 것입니다.

|수|약수|약수의 개수|
|-----|-----|-----|
|13|1, 13|2|
|14|1, 2, 7, 14|4|
|15|1, 3, 5, 15|4|
|16|1, 2, 4, 8, 16|5|
|17|1, 17|2|

* 따라서, 13 + 14 + 15 - 16 + 17 = 43을 return 해야 합니다.

**예제 #2**  
* 다음 표는 24부터 27까지의 수들의 약수를 모두 나타낸 것입니다.

|수|약수|약수의 개수|
|-----|-----|-----|
|24|1, 2, 3, 4, 6, 8, 12, 24|8|
|25|1, 5, 25|3|
|26|1, 2, 13, 26|4|
|27|1, 3, 9, 27|4|

* 따라서, 24 - 25 + 26 + 27 = 52를 return 해야 합니다.


### 문제풀이
1. 수가 주어지면 1과 자기 자신의 수는 무조건 약수이므로 초기화를 해준다.
2. 2부터 수의 제곱근까지 나누었을때 나눠지면 몫과 나눈 값이 약수이므로 measure_list에 add해준다.
	* set으로 초기화 한 이유는 같은 숫자가 2개가 들어갈 수도 있기 때문이다.
		* ex) 16의 약수중 4가 이와같이 해당된다.
3. 약수의 개수를 얻어와서 짝수면 더해주고 아니면 빼준다.

### 코드
```python
def get_measure_count(num):
    sqrt = int(num ** 0.5) # 제곱근 구하는 방법
    measure_list = {1, num}

    for i in range(2, int(sqrt+1)):
        if num % i == 0:
            measure_list.add(i)
            measure_list.add(num // i)

    return len(measure_list)

def solution(left, right):
    answer = 0

    for num in range(left, right+1):
        if get_measure_count(num) % 2 == 0:
            answer += num
        else:
            answer -= num

    return answer
```
