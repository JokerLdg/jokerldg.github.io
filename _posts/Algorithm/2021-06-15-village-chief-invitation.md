---
layout: post
title: 백준 9237번 이장님 초대 (python 파이썬)
subtitle: 백준 9237번 이장님 초대
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 9237번 이장님 초대 문제를 Python으로 해결한 문제이다.  

* [백준 9237번 이장님 초대 문제 링크](https://www.acmicpc.net/problem/9237){:target="_blank"}


### 문제 
농부 상근이는 마당에 심기 위한 나무 묘목 n개를 구입했다. 묘목 하나를 심는데 걸리는 시간은 1일이고, 상근이는 각 묘목이 다 자라는데 며칠이 걸리는지 정확하게 알고 있다.

상근이는 마을 이장님을 초대해 자신이 심은 나무를 자랑하려고 한다. 이장님을 실망시키면 안되기 때문에, 모든 나무가 완전히 자란 이후에 이장님을 초대하려고 한다. 즉, 마지막 나무가 다 자란 다음날 이장님을 초대할 것이다.

상근이는 나무를 심는 순서를 신중하게 골라 이장님을 최대한 빨리 초대하려고 한다. 이장님을 며칠에 초대할 수 있을까?


### 입력
입력은 두 줄로 이루어져 있다. 첫째 줄에는 묘목의 수 N (1 ≤ N ≤ 100,000)이 주어진다. 둘째 줄에는 각 나무가 다 자라는데 며칠이 걸리는지를 나타낸 ti가 주어진다. (1 ≤ ti ≤ 1,000,000)


### 출력
**<u>첫째 줄에 며칠에 이장님을 초대할 수 있는지 출력한다. 답이 여러 가지인 경우에는 가장 작은 값을 출력한다. 묘목을 구입한 날이 1일이다.</u>**


### 문제풀이
문제에 보면 마지막 나무가 다 자란 다음날 이장님을 초대할 것이다. 라는 문구가 있다.
결국 첫 나무를 다 심으면 2일이라는 것이다.

1. 나무가 걸리는 일수를 내림차순으로 정렬한다.
2. enumerate를 이용하여 인덱스와 값을 이용하면 되는데, 주의할 점은 index+value+2이다. 
    * +2를 하는 이유는 나무를 다 심으면 2일이기 때문에 마지막에 2라는 값을 더하는 것이다.
3. index+value+2를 이용하여 answer변수에 담아주는데 max를 이용하여 가장 큰값을 넣어주면 된다.


### 코드
```python
import sys

read = sys.stdin.readline

N = read()
tree = sorted(list(map(int, read().split())), reverse=True)
answer = 0

for index, value in enumerate(tree):
    answer = max(answer, index + value + 2)

print(answer)
```