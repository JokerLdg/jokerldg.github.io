---
layout: post
title: 백준 5545번 최고의 피자 (python 파이썬)
subtitle: 백준 5545번 최고의 피자
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 5545번 최고의 피자 문제를 Python으로 해결한 문제이다.  

* [백준 5545번 최고의 피자 문제 링크](https://www.acmicpc.net/problem/5545){:target="_blank"}


### 문제 
상근이는 근처 피자 가게에서 매일 저녁으로 피자를 배달해 먹는다. 주머니 사정이 얇아진 상근이는 이번 달부터는 "최고의 피자"를 구매하려고 한다. 최고의 피자란, 피자 가게에서 주문할 수 있는 피자 중 1원당 열량이 가장 높은 피자를 말한다. 최고의 피자는 여러 종류가 있을 수도 있다.

이 피자 가게는 토핑 N개에서 여러 종류를 선택해서 주문할 수 있다. 같은 종류의 토핑을 2개 이상 선택할 수는 없다. 또, 토핑을 전혀 선택하지 않을 수도 있다.

선택한 토핑은 도우 위에 올라간다. 도우의 가격은 A원이고, 토핑의 가격은 모두 B원이다. 피자의 가격은 도우와 토핑의 가격의 합계가 된다. 즉, 토핑을 k종류 (0 ≤ k ≤ N) 선택했다면, 피자의 가격은 A + B * k원이 된다. 피자의 열량은 도우와 토핑의 열량의 합이다.

도우의 가격, 토핑의 가격, 그리고 도우와 각 토핑의 열량 값이 주어졌을 때, 최고의 피자의 1원 당 열량을 구하는 프로그램을 작성하시오.


### 입력
첫째 줄에 토핑의 종류의 수 N(1 ≤ N ≤ 100)이 주어진다. 둘째 줄에는 도우의 가격 A와 토핑의 가격 B가 주어진다. (1 ≤ A, B ≤ 1000) 셋째 줄에는 도우의 열량 C가 주어진다. (1 ≤ C ≤ 10000) 다음 줄부터 N개 줄에는 각 토핑의 열량 Di가 한 줄에 하나씩 주어진다. (1 ≤ Di ≤ 10000)


### 출력
**<u>첫째 줄에 최고의 피자의 1원 당 열량을 출력한다. 소수점 이하는 버리고 정수 값으로 출력한다.</u>**


### 문제풀이
토핑들의 칼로리를 내림차순으로 정렬한다.

1. 토핑들의 개수만큼 반복을 돌리는데, 칼로리에 C + sum(D[0:i]) 더해주고, 가격에는 A + (B * i)를 해준다.
2. 칼로리 / 가격의 값이 이전에 저장한 값보다 크다면 값을 바꿔준다.
    * 값이 만약 떨어진다면 종료시킨다. 내림차순이기 때문에 값이 떨어지면 다음부터는 볼 필요가 없다.


### 코드
```python
import sys

read = lambda: sys.stdin.readline().rstrip()

N = int(read())
A, B = map(int, read().split())
C = int(read())
D = []

for _ in range(N):
    D.append(int(read()))

D.sort(reverse=True)

answer = C / A

for i in range(1, len(D)+1):
    calorie = C + sum(D[0:i])
    price = A + (B * i)

    if calorie / price > answer:
        answer = calorie / price
    else:
        break

print(int(answer))
```