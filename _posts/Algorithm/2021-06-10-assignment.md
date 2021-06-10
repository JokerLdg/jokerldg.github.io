---
layout: post
title: 백준 13904번 과제 (python 파이썬)
subtitle: 백준 13904번 과제
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 13904번 과제 문제를 Python으로 해결한 문제이다.  

* [백준 13904번 과제 문제 링크](https://www.acmicpc.net/problem/13904){:target="_blank"}


### 문제 
웅찬이는 과제가 많다. 하루에 한 과제를 끝낼 수 있는데, 과제마다 마감일이 있으므로 모든 과제를 끝내지 못할 수도 있다. 과제마다 끝냈을 때 얻을 수 있는 점수가 있는데, 마감일이 지난 과제는 점수를 받을 수 없다.

웅찬이는 가장 점수를 많이 받을 수 있도록 과제를 수행하고 싶다. 웅찬이를 도와 얻을 수 있는 점수의 최댓값을 구하시오.


### 입력
첫 줄에 정수 N (1 ≤ N ≤ 1,000)이 주어진다.

다음 줄부터 N개의 줄에는 각각 두 정수 d (1 ≤ d ≤ 1,000)와 w (1 ≤ w ≤ 100)가 주어진다. d는 과제 마감일까지 남은 일수를 의미하며, w는 과제의 점수를 의미한다.


### 출력
**<u>얻을 수 있는 점수의 최댓값을 출력한다.</u>**


### 문제풀이
과제의 점수를 최댓값으로 만들어야 한다.

최댓값으로 만들기 위해서는 과제의 점수가 가장 큰 것부터 해결하고 최대한 많은 과제를 해결하기 위해 과제 기간의 마지막날 부터 채워 넣으면 된다.

heapq 리스트에 [-value, day, value]를 삽입하여 과제 점수가 가장 큰 것부터 접근 할 수 있도록 한다.

heapq 리스트가 모두 없어질 때까지 반복하며 내부 반복문에서 기간의 마지막일 부터 접근하여 sums가 0일때, 즉 그날에 과제를 하지 않았으면 그날에 과제를 수행하고 sums의 값을 더한다.

반복문이 끝나고 sums 리스트의 총 합을 출력한다.


### 코드
```python
import sys
import heapq

N = int(input())
reports = []
answer = [0] * 1001 # N 개의 최대값 +1 만큼 해준다.

for _ in range(N):
    day, value = map(int, sys.stdin.readline().split())
    reports.append([-value, day, value])

heapq.heapify(reports)

while reports:
    temp = heapq.heappop(reports)
    for i in range(temp[1], 0, -1):
        if answer[i] == 0:
            answer[i] = temp[2]
            break

print(sum(answer))
```