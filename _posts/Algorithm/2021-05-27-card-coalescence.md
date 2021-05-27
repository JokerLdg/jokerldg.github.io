---
layout: post
title: 백준 15903번 카드 합체 놀이 (python 파이썬)
subtitle: 백준 15903번 카드 합체 놀이
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 15903번 카드 합체 놀이 문제를 Python으로 해결한 문제이다.  

* [백준 15903번 카드 합체 놀이 문제 링크](https://www.acmicpc.net/problem/15903){:target="_blank"}


### 문제 
석환이는 아기다. 아기 석환이는 자연수가 쓰여져있는 카드를 갖고 다양한 놀이를 하며 노는 것을 좋아한다. 오늘 아기 석환이는 무슨 놀이를 하고 있을까? 바로 카드 합체 놀이이다!

아기 석환이는 자연수가 쓰여진 카드를 n장 갖고 있다. 처음에 i번 카드엔 ai가 쓰여있다. 카드 합체 놀이는 이 카드들을 합체하며 노는 놀이이다. 카드 합체는 다음과 같은 과정으로 이루어진다.

1. x번 카드와 y번 카드를 골라 그 두 장에 쓰여진 수를 더한 값을 계산한다. (x ≠ y)
2. 계산한 값을 x번 카드와 y번 카드 두 장 모두에 덮어 쓴다.

이 카드 합체를 총 m번 하면 놀이가 끝난다. m번의 합체를 모두 끝낸 뒤, n장의 카드에 쓰여있는 수를 모두 더한 값이 이 놀이의 점수가 된다. 이 점수를 가장 작게 만드는 것이 놀이의 목표이다.

아기 석환이는 수학을 좋아하긴 하지만, 아직 아기이기 때문에 점수를 얼마나 작게 만들 수 있는지를 알 수는 없었다(어른 석환이는 당연히 쉽게 알 수 있다). 그래서 문제 해결 능력이 뛰어난 여러분에게 도움을 요청했다. 만들 수 있는 가장 작은 점수를 계산하는 프로그램을 만들어보자.


### 입력
첫 번째 줄에 카드의 개수를 나타내는 수 n(2 ≤ n ≤ 1,000)과 카드 합체를 몇 번 하는지를 나타내는 수 m(0 ≤ m ≤ 15×n)이 주어진다.

두 번째 줄에 맨 처음 카드의 상태를 나타내는 n개의 자연수 a1, a2, …, an이 공백으로 구분되어 주어진다. (1 ≤ ai ≤ 1,000,000)

### 출력
**<u>첫 번째 줄에 만들 수 있는 가장 작은 점수를 출력한다.</u>**

### 문제풀이
1. 큐를 이용하여 문제를 풀었다.
2. 배열을 힙으로 만둘어주는 heapify() 함수를 이용하여 힙을 만들어준다.
3. m만큼 가장 작은 값 두개를 빼서 더하고 그 값을 두번씩 넣어준다.
4. 마지막 cards를 다 더하면 된다.

### 코드
```python
import heapq

n, m = map(int, input().split())

cards = [int(x) for x in input().split()]
heapq.heapify(cards)

for _ in range(m):
    card1 = heapq.heappop(cards)
    card2 = heapq.heappop(cards)

    heapq.heappush(cards, card1 + card2)
    heapq.heappush(cards, card1 + card2)

print(sum(cards))
```