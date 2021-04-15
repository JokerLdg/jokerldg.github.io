---
layout: post
title: 프로그래머스 제일 작은 수 제거하기 (python 파이썬)
subtitle: 프로그래머스 제일 작은 수 제거하기
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 제일 작은 수 제거하기 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 제일 작은 수 제거하기 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12935){:target="_blank"}

### 문제 
정수를 저장한 배열, arr 에서 가장 작은 수를 제거한 배열을 리턴하는 함수, solution을 완성해주세요. 단, 리턴하려는 배열이 빈 배열인 경우엔 배열에 -1을 채워 리턴하세요. 예를들어 arr이 [4,3,2,1]인 경우는 [4,3,2]를 리턴 하고, [10]면 [-1]을 리턴 합니다.

### 제한사항
* arr은 길이 1 이상인 배열입니다.
* 인덱스 i, j에 대해 i ≠ j이면 arr[i] ≠ arr[j] 입니다.

### 입출력 예

|arr|return|
|-----|-----|
|[4,3,2,1]|[4,3,2]|
|[10]|[-1]|


### 문제풀이
* 배열의 길이가 1이면 배열을 새로 만든후 -1을 집어넣어준다.
* 배열에서 가장작은값을 remove로 지워준다.

### 코드
```python
def solution(arr):

    if len(arr) == 1:
        arr = []
        arr.append(-1)
    else:
        arr.remove(min(arr))

    return arr
```
