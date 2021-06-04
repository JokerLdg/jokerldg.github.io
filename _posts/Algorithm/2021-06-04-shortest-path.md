---
layout: post
title: 백준 1753번 최단경로 (python 파이썬)
subtitle: 백준 1753번 최단경로
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 1753번 최단경로 문제를 Python으로 해결한 문제이다.  

* [백준 1753번 최단경로 문제 링크](https://www.acmicpc.net/problem/1753){:target="_blank"}


### 문제 
방향그래프가 주어지면 주어진 시작점에서 다른 모든 정점으로의 최단 경로를 구하는 프로그램을 작성하시오. 단, 모든 간선의 가중치는 10 이하의 자연수이다.


### 입력
첫째 줄에 정점의 개수 V와 간선의 개수 E가 주어진다. (1≤V≤20,000, 1≤E≤300,000) 모든 정점에는 1부터 V까지 번호가 매겨져 있다고 가정한다. 둘째 줄에는 시작 정점의 번호 K(1≤K≤V)가 주어진다. 셋째 줄부터 E개의 줄에 걸쳐 각 간선을 나타내는 세 개의 정수 (u, v, w)가 순서대로 주어진다. 이는 u에서 v로 가는 가중치 w인 간선이 존재한다는 뜻이다. u와 v는 서로 다르며 w는 10 이하의 자연수이다. 서로 다른 두 정점 사이에 여러 개의 간선이 존재할 수도 있음에 유의한다.


### 출력
**<u>첫째 줄부터 V개의 줄에 걸쳐, i번째 줄에 i번 정점으로의 최단 경로의 경로값을 출력한다. 시작점 자신은 0으로 출력하고, 경로가 존재하지 않는 경우에는 INF를 출력하면 된다.</u>**


### 문제풀이
다익스트라 알고리즘을 이용하여 풀이한 문제이다.

1. 비용을 미리 무한대로 초기화 한다. (정점의 개수 + 1개 만큼)
2. queue를 이용하여 queue의 시작값에 0을 넣어준다.
	* 자기 자신의 비용이 0이기 때문에 처음을 0으로 초기화 해준다.
3. 큐에서 현재 노드, 현재 가중치를 꺼낸다.
4. 최단 거리가 아닌경우는 스킵한다.
5. 그리고 현재 노드에서 다음 노드와 인접 노드로 가는 가중치 계산의 반복을 진행한다.
	* 기존의 최소 가중치 보다 더 작으면 교체해준다.
	* 다음 노드에 가중치를 넣어준다.


### 코드
```python
import sys
import heapq

INF = float('inf')
V, E = map(int, sys.stdin.readline().split())
K = int(sys.stdin.readline())
graph = [[] for _ in range(V + 1)]
# 비용을 미리 무한대로 초기화
answer = [INF] * (V + 1)
queue = []

# 경로 입력
for i in range(E):
    u, v, w = map(int, sys.stdin.readline().split())
    graph[u].append([v, w])

def dijkstra(start):
    answer[start] = 0 # 자기 자신의 비용은 0이기 때문에 처음 부분은 0으로 초기화
    heapq.heappush(queue, [0, start]) # 시작값을 0 으로 초기화(자기 자신이기 때문)

    while queue:
        # 현재 노드, 현재 가중치를 pop한다.
        current_w, current_node = heapq.heappop(queue)

        # 최단 거리가 아닌경우 스킵
        if answer[current_node] < current_w:
            continue

        for next_node, weight in graph[current_node]:
            # 선택된 노드 거쳐서 인접 노드로 가는 가중치
            next_w = current_w + weight

            # 기존의 최소 가중치 보다 더 작다면 교체한다.
            # 그리고 다음 노드에 다음 가중치를 넣어준다.
            if next_w < answer[next_node]:
                answer[next_node] = next_w
                heapq.heappush(queue, [next_w, next_node])

dijkstra(K)

# 첫번째 부터 출력(0번째는 필요 없는값이기 때문에)
for i in answer[1:]:
    print(i if i != INF else "INF")
```