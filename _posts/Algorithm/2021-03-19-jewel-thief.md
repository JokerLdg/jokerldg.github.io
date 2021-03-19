---
layout: post
title: 백준 1202번 보석 도둑 (python 파이썬)
subtitle: 백준 1202번 문제 보석 도둑
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 1202번 보석 도둑 문제를 Python으로 해결한 문제이다.  

* [백준 1202번 보석 도둑 문제 링크](https://www.acmicpc.net/problem/1202){:target="_blank"}

### 문제 
세계적인 도둑 상덕이는 보석점을 털기로 결심했다.

상덕이가 털 보석점에는 보석이 총 N개 있다. 각 보석은 무게 Mi와 가격 Vi를 가지고 있다. 상덕이는 가방을 K개 가지고 있고, 각 가방에 담을 수 있는 최대 무게는 Ci이다. 가방에는 최대 한 개의 보석만 넣을 수 있다.

**<u>상덕이가 훔칠 수 있는 보석의 최대 가격을 구하는 프로그램을 작성하시오.</u>**


### 입력
첫째 줄에 N과 K가 주어진다. (1 ≤ N, K ≤ 300,000)

다음 N개 줄에는 각 보석의 정보 Mi와 Vi가 주어진다. (0 ≤ Mi, Vi ≤ 1,000,000)

다음 K개 줄에는 가방에 담을 수 있는 최대 무게 Ci가 주어진다. (1 ≤ Ci ≤ 100,000,000)

모든 숫자는 양의 정수이다.

### 출력
**<u>첫째 줄에 상덕이가 훔칠 수 있는 보석 가격의 합의 최댓값을 출력한다.</u>**

### 문제풀이
이 문제는 보석의 정보와 무게와 가방의 개수가 주어졌을때 보석의 최대 가격을 출력하는 문제이다.

**<u>접근방법</u>**  
해당 문제는 우선순위 큐를 이용하여 풀 수 있다.

**가장 작은 무게를 수용할 수 있는 가방(=capacity) 이하의 모든 보석(capable_gem) 중 가장 값이 큰 것을 뽑아내고 이를 가방이 끝날 때 까지 반복하는 것이 포인트다.**

1. weights의 우선순위 큐에서 최솟값을 뺀다.    
2. **수용량 이하 무게의 모든 보석 gem을 capable_gem에 무게를 제외한 값을 -로 넣어준다. -를 붙이는 이유는 최소 힙형태로 만들어서 맨앞에서부터 빼내려고 하는 이유이다.**  
3. capacity 이하의 모든 무게의 보석을 꺼냈으면 capable_gem(최대 힙)중 가장 큰 값을 꺼낸 뒤 sum 값에서 빼준다.  
4. 1~3를 반복한 뒤 weights에 더 이상 없거나, gem과 capable_gem 모두 비었으면 while문을 끝낸다.  

### 코드
```python
import sys
import heapq
input = sys.stdin.readline

N, K = map(int, input().split())

gem = []
weights = []

for _ in range(N):
  M,V = map(int, input().split())
  heapq.heappush(gem, [M,V])

for _ in range(K):
  heapq.heappush(weights, int(input()))

sum = 0

capable_gem = []

for _ in range(K):
  capacity = heapq.heappop(weights)
  
  while gem and capacity >= gem[0][0]:
    [weight, price] = heapq.heappop(gem)
    heapq.heappush(capable_gem, -price)
  
  if capable_gem:
    sum -= heapq.heappop(capable_gem)
  elif not gem:
    break

print(sum)
```