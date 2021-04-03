---
layout: post
title: 프로그래머스 같은 숫자는 싫어 (python 파이썬)
subtitle: 프로그래머스 같은 숫자는 싫어
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 같은 숫자는 싫어 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 같은 숫자는 싫어 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12906){:target="_blank"}

### 문제 
배열 arr가 주어집니다. 배열 arr의 각 원소는 숫자 0부터 9까지로 이루어져 있습니다. 이때, 배열 arr에서 연속적으로 나타나는 숫자는 하나만 남기고 전부 제거하려고 합니다. 단, 제거된 후 남은 수들을 반환할 때는 배열 arr의 원소들의 순서를 유지해야 합니다. 예를 들면,

* arr = [1, 1, 3, 3, 0, 1, 1] 이면 [1, 3, 0, 1] 을 return 합니다.
* arr = [4, 4, 4, 3, 3] 이면 [4, 3] 을 return 합니다.
배열 arr에서 연속적으로 나타나는 숫자는 제거하고 남은 수들을 return 하는 solution 함수를 완성해 주세요.

### 제한사항
* 배열 arr의 크기 : 1,000,000 이하의 자연수
* 배열 arr의 원소의 크기 : 0보다 크거나 같고 9보다 작거나 같은 정수


### 입출력 예

|arr|answer|
|-----|-----|
|[1,1,3,3,0,1,1]|[1,3,0,1]|
|[4,4,4,3,3]|[4,3]|


### 문제풀이
* 먼저 첫번째 값을 배열에 넣어준다.
* 이전값과 현재값을 비교하여 틀리면 배열에 추가해준다.


### 코드
```python
def solution(arr):
    answer = []
    answer.append(arr[0])
    
    for i in range(1, len(arr)):  
        if arr[i-1] != arr[i]:
          answer.append(arr[i])

    return answer
```