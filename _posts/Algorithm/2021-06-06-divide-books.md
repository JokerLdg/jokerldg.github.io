---
layout: post
title: 백준 9576번 책 나눠주기 (python 파이썬)
subtitle: 백준 9576번 책 나눠주기
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 9576번 책 나눠주기 문제를 Python으로 해결한 문제이다.  

* [백준 9576번 책 나눠주기 문제 링크](https://www.acmicpc.net/problem/9576){:target="_blank"}


### 문제 
백준이는 방 청소를 하면서 필요 없는 전공 서적을 사람들에게 나눠주려고 한다. 나눠줄 책을 모아보니 총 N권이었다. 책이 너무 많기 때문에 백준이는 책을 구분하기 위해 각각 1부터 N까지의 정수 번호를 중복되지 않게 매겨 두었다.

조사를 해 보니 책을 원하는 서강대학교 학부생이 총 M명이었다. 백준이는 이 M명에게 신청서에 두 정수 a, b (1 ≤ a ≤ b ≤ N)를 적어 내라고 했다. 그러면 백준이는 책 번호가 a 이상 b 이하인 책 중 남아있는 책 한 권을 골라 그 학생에게 준다. 만약 a번부터 b번까지의 모든 책을 이미 다른 학생에게 주고 없다면 그 학생에게는 책을 주지 않는다.

백준이가 책을 줄 수 있는 최대 학생 수를 구하시오.


### 입력
첫째 줄에 테스트 케이스의 수가 주어진다.

각 케이스의 첫 줄에 정수 N(1 ≤ N ≤ 1,000)과 M(1 ≤ M ≤ 1,000)이 주어진다. 다음 줄부터 M개의 줄에는 각각 정수 ai, bi가 주어진다. (1 ≤ ai ≤ bi ≤ N)


### 출력
**<u>각 테스트 케이스마다 백준이가 책을 줄 수 있는 최대 학생 수를 한 줄에 하나씩 출력한다.</u>**


### 문제풀이
1. b를 기준으로 오름차순으로 정렬한다.
2. a,b를 리스트에서 꺼낸다.
3. a부터 b까지 반복을 돌리는데, books[i]번째 책을 안나눠주었으면 True로 바꾸고 cnt변수를 1증가 시키고 break한다.
4. 1 ~ 3을 반복한다.

### 코드
```python
import sys

T = int(input())

for _ in range(T):
    N, M = map(int, sys.stdin.readline().split())

    books = [False] * (N+1)
    req = []

    for _ in range(M):
        req.append(list(map(int, sys.stdin.readline().split())))
    req.sort(key=lambda x: x[1])

    cnt = 0

    for a, b in req:
        for i in range(a, b+1):
            if not books[i]:
                cnt += 1
                books[i] = True
                break

    print(cnt)
```