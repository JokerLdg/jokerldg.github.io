---
layout: post
title: 프로그래머스 타겟 넘버 (python 파이썬)
subtitle: 프로그래머스 타겟 넘버
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 타겟 넘버 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 타겟 넘버 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/43165){:target="_blank"}


### 문제 설명
n개의 음이 아닌 정수가 있습니다. 이 수를 적절히 더하거나 빼서 타겟 넘버를 만들려고 합니다. 예를 들어 [1, 1, 1, 1, 1]로 숫자 3을 만들려면 다음 다섯 방법을 쓸 수 있습니다.

```
-1+1+1+1+1 = 3
+1-1+1+1+1 = 3
+1+1-1+1+1 = 3
+1+1+1-1+1 = 3
+1+1+1+1-1 = 3
```
사용할 수 있는 숫자가 담긴 배열 numbers, 타겟 넘버 target이 매개변수로 주어질 때 숫자를 적절히 더하고 빼서 타겟 넘버를 만드는 방법의 수를 return 하도록 solution 함수를 작성해주세요.


### 제한사항
* 주어지는 숫자의 개수는 2개 이상 20개 이하입니다.
* 각 숫자는 1 이상 50 이하인 자연수입니다.
* 타겟 넘버는 1 이상 1000 이하인 자연수입니다.


### 입출력 예

|numbers|target|return|
|-----|-----|-----|
|[1,1,1,1,1]|3|5|


### 입출력 예 설명
문제에 나온 예와 같습니다.


### 문제풀이
* 해당문제는 dfs를 이용하여 풀어보았다.
* dfs로 각 숫자를 더하는것과 빼는것 두개를 동시에 진행하면 된다.

### 코드
```python
def solution(numbers, target):
    n = len(numbers)
    answer = 0

    def dfs(idx, result):
        if idx == n:
            if result == target:
                nonlocal answer
                answer += 1
            return
        else:
            dfs(idx+1, result+numbers[idx])
            dfs(idx+1, result-numbers[idx])

    dfs(0,0)

    return answer
```
