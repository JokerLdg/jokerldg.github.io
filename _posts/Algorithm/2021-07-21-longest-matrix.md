---
layout: post
title: 백준 11053번 가장 긴 증가하는 부분 수열 (python 파이썬)
subtitle: 백준 11053번 가장 긴 증가하는 부분 수열
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 11053번 가장 긴 증가하는 부분 수열 문제를 Python으로 해결한 문제이다.  

* [백준 11053번 가장 긴 증가하는 부분 수열 문제 링크](https://www.acmicpc.net/problem/11053){:target="_blank"}


### 문제 
수열 A가 주어졌을 때, 가장 긴 증가하는 부분 수열을 구하는 프로그램을 작성하시오.

예를 들어, 수열 A = {10, 20, 10, 30, 20, 50} 인 경우에 가장 긴 증가하는 부분 수열은 A = {**10**, **20**, 10, **30**, 20, **50**} 이고, 길이는 4이다.


### 입력
첫째 줄에 수열 A의 크기 N (1 ≤ N ≤ 1,000)이 주어진다.

둘째 줄에는 수열 A를 이루고 있는 Ai가 주어진다. (1 ≤ Ai ≤ 1,000)


### 출력
**<u>첫째 줄에 수열 A의 가장 긴 증가하는 부분 수열의 길이를 출력한다.</u>**


### 문제풀이
DP로 풀어도 풀리지만 N^2의 시간복잡도를 가지기 때문에 더 빠른 이진 탐색(n log n) 풀이로 풀어보았다.

1. dp를 A[0]으로 초기화한다.
2. 현재 위치(i)가 이전 위치의 원소들보다 크면 dp에 추가한다.
3. 현재 위치(i)가 이전 위치의 원소보다 작거나 같으면, 
    * bisect.bisect_left로 이전 위치의 원소 중 가장 큰 원소의 index값을 구한다. 
    * dp의 index 원소를 arr[i]로 바꿔준다.
4. dp의 길이를 출력한다.
    * **정답은 4가 된다.**


### 코드
```python
import sys
import bisect

read = lambda: sys.stdin.readline().rstrip()

N = int(read())
A = list(map(int, read().split()))

dp = [A[0]]

for i in range(1, N):
    if A[i] > dp[-1]:
        dp.append(A[i])
    else:
        idx = bisect.bisect_left(dp, A[i])
        dp[idx] = A[i]

print(len(dp))
```