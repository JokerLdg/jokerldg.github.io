---
layout: post
title: 백준 13164번 행복 유치원 (python 파이썬)
subtitle: 백준 13164번 행복 유치원
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 13164번 행복 유치원 문제를 Python으로 해결한 문제이다.  

* [백준 13164번 행복 유치원 문제 링크](https://www.acmicpc.net/problem/13164){:target="_blank"}


### 문제 
행복 유치원 원장인 태양이는 어느 날 N명의 원생들을 키 순서대로 일렬로 줄 세우고, 총 K개의 조로 나누려고 한다. 각 조에는 원생이 적어도 한 명 있어야 하며, 같은 조에 속한 원생들은 서로 인접해 있어야 한다. 조별로 인원수가 같을 필요는 없다.

이렇게 나뉘어진 조들은 각자 단체 티셔츠를 맞추려고 한다. 조마다 티셔츠를 맞추는 비용은 조에서 가장 키가 큰 원생과 가장 키가 작은 원생의 키 차이만큼 든다. 최대한 비용을 아끼고 싶어 하는 태양이는 K개의 조에 대해 티셔츠 만드는 비용의 합을 최소로 하고 싶어한다. 태양이를 도와 최소의 비용을 구하자.


### 입력
입력의 첫 줄에는 유치원에 있는 원생의 수를 나타내는 자연수 N(1 ≤ N ≤ 300,000)과 나누려고 하는 조의 개수를 나타내는 자연수 K(1 ≤ K ≤ N)가 공백으로 구분되어 주어진다. 다음 줄에는 원생들의 키를 나타내는 N개의 자연수가 공백으로 구분되어 줄 서 있는 순서대로 주어진다. 태양이는 원생들을 키 순서대로 줄 세웠으므로, 왼쪽에 있는 원생이 오른쪽에 있는 원생보다 크지 않다. 원생의 키는 10^9를 넘지 않는 자연수이다.


### 출력
**<u>티셔츠 만드는 비용이 최소가 되도록 K개의 조로 나누었을 때, 티셔츠 만드는 비용을 출력한다.</u>**


### 문제풀이
N명의 학생들을 K개의 그룹으로 나눈다고 했을 때 달리 말하면 N-K 개의 키 차이를 무시할 수 있다는 것이다.  

1. 각 학생들의 차를 구해서 costs 변수에 넣어주고, 비용이 작은순으로 정렬한다.
2. 그리고 N-K개의 키 차이를 무시 할 수 있으니, costs[:N-K]만큼 합을 구해주면 된다.


### 코드
```python
import sys

read = lambda: sys.stdin.readline().rstrip()

N, K = map(int, read().split())
kindergartens = list(map(int, read().split()))

costs = []

for i in range(N-1):
    costs.append(kindergartens[i+1] - kindergartens[i])

costs.sort()

print(sum(costs[:N-K]))
```