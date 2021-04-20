---
layout: post
title: 프로그래머스 행렬의 덧셈 (python 파이썬)
subtitle: 프로그래머스 행렬의 덧셈
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 행렬의 덧셈 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 행렬의 덧셈 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12950){:target="_blank"}

### 문제 
행렬의 덧셈은 행과 열의 크기가 같은 두 행렬의 같은 행, 같은 열의 값을 서로 더한 결과가 됩니다. 2개의 행렬 arr1과 arr2를 입력받아, 행렬 덧셈의 결과를 반환하는 함수, solution을 완성해주세요.

### 제한사항
* 행렬 arr1, arr2의 행과 열의 길이는 500을 넘지 않습니다.

### 입출력 예

|arr1|arr2|return|
|-----|-----|-----|
|[[1,2],[2,3]]|[[3,4],[5,6]]|[[4,6],[7,9]]|
|[[1],[2]]|[[3],[4]]|[[4],[6]]|


### 문제풀이
* 이중 반복문을 이용하여 각 배열의 값을 더하여 배열로 만들어준다.

### 코드
```python
def solution(arr1, arr2):
    answer = arr1

    for i in range(len(arr1)):
        for j in range(len(arr1[i])):
            answer[i][j] = arr1[i][j] + arr2[i][j]

    return answer
```
