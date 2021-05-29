---
layout: post
title: 백준 11000번 강의실 배정 (python 파이썬)
subtitle: 백준 11000번 강의실 배정
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 11000번 강의실 배정 문제를 Python으로 해결한 문제이다.  

* [백준 11000번 강의실 배정 문제 링크](https://www.acmicpc.net/problem/11000){:target="_blank"}


### 문제 
수강신청의 마스터 김종혜 선생님에게 새로운 과제가 주어졌다. 

김종혜 선생님한테는 Si에 시작해서 Ti에 끝나는 N개의 수업이 주어지는데, 최소의 강의실을 사용해서 모든 수업을 가능하게 해야 한다. 

참고로, 수업이 끝난 직후에 다음 수업을 시작할 수 있다. (즉, Ti ≤ Sj 일 경우 i 수업과 j 수업은 같이 들을 수 있다.)

수강신청 대충한 게 찔리면, 선생님을 도와드리자!


### 입력
첫 번째 줄에 N이 주어진다. (1 ≤ N ≤ 200,000)

이후 N개의 줄에 Si, Ti가 주어진다. (1 ≤ Si < Ti ≤ 109)

### 출력
**<u>강의실의 개수를 출력하라.</u>**

### 문제풀이
heapq를 이용하여 문제를 풀어보았다.

1. 먼저 순서대로 time_table변수에 값을 넣어준다.
	* 이때 sys.stdin.readline()을 이용한 이유는 사용을 안하면 시간초과가 나게된다.
2. time_table을 시작시간 기준으로 오름차순 정렬한다.
3. queue를 생성하여 첫번째 강의의 끝나는 시간을 넣어준다.
4. 순서대로 time_table을 도는데, 큐의 첫번째 값이 강의시간의 시작값보다 작거나 같으면 queue에서 빼주고 아니면 값을 넣는다.
5. queue의 길이를 출력한다.


### 코드
```python
import heapq
import sys

N = int(input())
time_table = []

for i in range(N):
    time_table.append(list(map(int, sys.stdin.readline().split())))

time_table.sort(key=lambda x: x[0])

queue = []
heapq.heappush(queue, time_table[0][1])

for i in range(1, N):
    if queue[0] <= time_table[i][0]:
        heapq.heappop(queue)
    heapq.heappush(queue, time_table[i][1])

print(len(queue))
```