---
layout: post
title: 프로그래머스 음양 더하기 (python 파이썬)
subtitle: 프로그래머스 음양 더하기
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 음양 더하기 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 음양 더하기 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/76501){:target="_blank"}


### 문제 설명
어떤 정수들이 있습니다. 이 정수들의 절댓값을 차례대로 담은 정수 배열 absolutes와 이 정수들의 부호를 차례대로 담은 불리언 배열 signs가 매개변수로 주어집니다. 실제 정수들의 합을 구하여 return 하도록 solution 함수를 완성해주세요.


### 제한사항
* absolutes의 길이는 1 이상 1,000 이하입니다.
    * absolutes의 모든 수는 각각 1 이상 1,000 이하입니다.
* signs의 길이는 absolutes의 길이와 같습니다.
    * ```signs[i]``` 가 참이면 ```absolutes[i]``` 의 실제 정수가 양수임을, 그렇지 않으면 음수임을 의미합니다.


### 입출력 예

|absolutes|signs|result|
|-----|-----|-----|
|[4,7,12]|[true,false,true]|9|
|[1,2,3]|[false,false,true]|0|


### 입출력 예 설명
**예제 #1**  
* signs가 ```[true,false,true]``` 이므로, 실제 수들의 값은 각각 4, -7, 12입니다.
* 따라서 세 수의 합인 9를 return 해야 합니다.

**예제 #2**  
* signs가 ```[false,false,true]``` 이므로, 실제 수들의 값은 각각 -1, -2, 3입니다.
* 따라서 세 수의 합인 0을 return 해야 합니다.


### 문제풀이
* zip을 이용하여 두개의 배열의 값을 확인한다.
* sign이 true이면 더하고, false이면 빼준다.

### 코드
```python
def solution(absolutes, signs):
    answer = 0

    for absolut, sign in zip(absolutes, signs):
        if sign:
            answer += absolut
        else:
            answer -= absolut

    return answer
```
