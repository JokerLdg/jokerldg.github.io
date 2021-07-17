---
layout: post
title: 백준 1149번 RGB거리 (python 파이썬)
subtitle: 백준 1149번 RGB거리
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 1149번 RGB거리 문제를 Python으로 해결한 문제이다.  

* [백준 1149번 RGB거리 문제 링크](https://www.acmicpc.net/problem/1149){:target="_blank"}


### 문제 
RGB거리에는 집이 N개 있다. 거리는 선분으로 나타낼 수 있고, 1번 집부터 N번 집이 순서대로 있다.

집은 빨강, 초록, 파랑 중 하나의 색으로 칠해야 한다. 각각의 집을 빨강, 초록, 파랑으로 칠하는 비용이 주어졌을 때, 아래 규칙을 만족하면서 모든 집을 칠하는 비용의 최솟값을 구해보자.

* 1번 집의 색은 2번 집의 색과 같지 않아야 한다.
* N번 집의 색은 N-1번 집의 색과 같지 않아야 한다.
* i(2 ≤ i ≤ N-1)번 집의 색은 i-1번, i+1번 집의 색과 같지 않아야 한다.

### 입력
첫째 줄에 집의 수 N(2 ≤ N ≤ 1,000)이 주어진다. 둘째 줄부터 N개의 줄에는 각 집을 빨강, 초록, 파랑으로 칠하는 비용이 1번 집부터 한 줄에 하나씩 주어진다. 집을 칠하는 비용은 1,000보다 작거나 같은 자연수이다.


### 출력
**<u>첫째 줄에 모든 집을 칠하는 비용의 최솟값을 출력한다.</u>**


### 문제풀이
빨간집, 초록집, 파란집인 경우를 계산하는데 그 이전의 값들 중에서 같은 색을 제외하고 최솟값을 더해주는걸 반복한다.
  
빨강, 초록, 파랑 집을 선택한 모든 경우에 대해 최솟값만이 더해져서 나오게 되며 이중에 최소 값을 선택하면 된다.

### 코드
```python
import sys

read = lambda: sys.stdin.readline().rstrip()

N = int(read())
RGB = []

for _ in range(N):
    RGB.append(list(map(int, read().split())))

for i in range(1, N):
    # 빨간집
    RGB[i][0] = min(RGB[i - 1][1], RGB[i - 1][2]) + RGB[i][0]

    # 초록집
    RGB[i][1] = min(RGB[i - 1][0], RGB[i - 1][2]) + RGB[i][1]

    # 파란집
    RGB[i][2] = min(RGB[i - 1][0], RGB[i - 1][1]) + RGB[i][2]

print(min(RGB[N - 1]))
```