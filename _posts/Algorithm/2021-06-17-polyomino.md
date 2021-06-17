---
layout: post
title: 백준 1343번 폴리오미노 (python 파이썬)
subtitle: 백준 1343번 폴리오미노
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 1343번 폴리오미노 문제를 Python으로 해결한 문제이다.  

* [백준 1343번 폴리오미노 문제 링크](https://www.acmicpc.net/problem/1343){:target="_blank"}


### 문제 
민식이는 다음과 같은 폴리오미노 2개를 무한개만큼 가지고 있다. AAAA와 BB

이제 '.'와 'X'로 이루어진 보드판이 주어졌을 때, 민식이는 겹침없이 'X'를 모두 폴리오미노로 덮으려고 한다. 이때, '.'는 폴리오미노로 덮으면 안 된다.

폴리오미노로 모두 덮은 보드판을 출력하는 프로그램을 작성하시오.


### 입력
첫째 줄에 보드판이 주어진다. 보드판의 크기는 최대 500이다.


### 출력
**<u>첫째 줄에 사전순으로 가장 앞서는 답을 출력한다. 만약 덮을 수 없으면 -1을 출력한다.</u>**


### 문제풀이
1. POLYOMINO dictionary를 {"XXXX": "AAAA", "XX": "BB"} 같이 만든다.
2. 반복문과 dictionary를 이용하여 입력값을 replace한다.
3. 반복문이 끝나고 입력값에 X가 포함되면 -1, 그게 아니면 입력값을 출력한다.


### 코드
```python
import sys

POLYOMINO = {
    "XXXX": "AAAA",
    "XX": "BB"
}

board = sys.stdin.readline().rstrip("\n")

for key in POLYOMINO.keys():
    board = board.replace(key, POLYOMINO.get(key))

if 'X' in board:
    print(-1)
else:
    print(board)
```