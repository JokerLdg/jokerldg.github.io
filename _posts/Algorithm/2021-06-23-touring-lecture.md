---
layout: post
title: 백준 2109번 순회강연 (python 파이썬)
subtitle: 백준 2109번 순회강연
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 2109번 순회강연 문제를 Python으로 해결한 문제이다.  

* [백준 2109번 순회강연 문제 링크](https://www.acmicpc.net/problem/2109){:target="_blank"}


### 문제 
한 저명한 학자에게 n(0 ≤ n ≤ 10,000)개의 대학에서 강연 요청을 해 왔다. 각 대학에서는 d(1 ≤ d ≤ 10,000)일 안에 와서 강연을 해 주면 p(1 ≤ p ≤ 10,000)만큼의 강연료를 지불하겠다고 알려왔다. 각 대학에서 제시하는 d와 p값은 서로 다를 수도 있다. 이 학자는 이를 바탕으로, 가장 많은 돈을 벌 수 있도록 순회강연을 하려 한다. 강연의 특성상, 이 학자는 하루에 최대 한 곳에서만 강연을 할 수 있다.

예를 들어 네 대학에서 제시한 p값이 각각 50, 10, 20, 30이고, d값이 차례로 2, 1, 2, 1 이라고 하자. 이럴 때에는 첫째 날에 4번 대학에서 강연을 하고, 둘째 날에 1번 대학에서 강연을 하면 80만큼의 돈을 벌 수 있다.


### 입력
첫째 줄에 정수 n이 주어진다. 다음 n개의 줄에는 각 대학에서 제시한 p값과 d값이 주어진다.


### 출력
**<u>첫째 줄에 최대로 벌 수 있는 돈을 출력한다.</u>**


### 문제풀이
1. 우선순위 큐를 이용하여 queue에 강연료를 넣어준다.
2. 날짜보다 queue의 길이가 더 크면 queue에서 pop한다.(우선순위 큐이기 때문에 작은값을 pop하게 됨)
3. queue의 합을 전부 더하여 출력한다.


### 코드
```python
import heapq
import sys

read = sys.stdin.readline

n = int(read().strip("\n"))

lectures = []

for _ in range(n):
    p, d = map(int, read().strip("\n").split())
    lectures.append([p, d])

lectures.sort(key = lambda x: x[1])

queue = []

for pay, day in lectures:
    heapq.heappush(queue, pay)

    if day < len(queue):
        heapq.heappop(queue)

print(sum(queue))
```