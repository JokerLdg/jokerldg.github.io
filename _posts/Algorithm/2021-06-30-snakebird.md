---
layout: post
title: 백준 16435번 스네이크버드 (python 파이썬)
subtitle: 백준 16435번 스네이크버드
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 16435번 스네이크버드 문제를 Python으로 해결한 문제이다.  

* [백준 16435번 스네이크버드 문제 링크](https://www.acmicpc.net/problem/16435){:target="_blank"}


### 문제 
스네이크버드는 뱀과 새의 모습을 닮은 귀여운 생물체입니다. 

스네이크버드의 주요 먹이는 과일이며 과일 하나를 먹으면 길이가 1만큼 늘어납니다.

과일들은 지상으로부터 일정 높이를 두고 떨어져 있으며 i (1 ≤ i ≤ N) 번째 과일의 높이는 hi입니다. 

스네이크버드는 자신의 길이보다 작거나 같은 높이에 있는 과일들을 먹을 수 있습니다.

스네이크버드의 처음 길이가 L일때 과일들을 먹어 늘릴 수 있는 최대 길이를 구하세요.


### 입력
첫 번째 줄에 과일의 개수 N (1 ≤ N ≤ 1,000) 과 스네이크버드의 초기 길이 정수 L (1 ≤ L ≤ 10,000) 이 주어집니다.

두 번째 줄에는 정수 h1, h2, ..., hN (1 ≤ hi ≤ 10,000) 이 주어집니다.


### 출력
**<u>첫 번째 줄에 스네이크버드의 최대 길이를 출력합니다.</u>**


### 문제풀이
1. N과 L을 입력받는다.
2. 과일의 높이를 입력받고, 과일의 높이를 오름차순으로 정렬한다.
3. 과일의 높이만큼 반복문을 돌리는데, 과일의 높이가 스네이크버드의 길이보다 크면 종료한다.
    * 과일의 높이가 크면 그 뒤의 값은 진행할 필요가 없기 때문이다.
4. 과일의 높이가 스네이크버드의 길이보다 작거나 같으면 스네이크버드의 길이를 1 증가시킨다. 


### 코드
```python
import sys

read = lambda: sys.stdin.readline().rstrip()

N, L = map(int, read().split())
h = list(map(int, read().split()))
h.sort()

for fruit in h:
    if fruit > L:
        break
    elif fruit <= L:
        L += 1

print(L)
```