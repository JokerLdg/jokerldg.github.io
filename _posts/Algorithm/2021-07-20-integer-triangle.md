---
layout: post
title: 백준 1932번 정수 삼각형 (python 파이썬)
subtitle: 백준 1932번 정수 삼각형
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 1932번 정수 삼각형 문제를 Python으로 해결한 문제이다.  

* [백준 1932번 정수 삼각형 문제 링크](https://www.acmicpc.net/problem/1932){:target="_blank"}


### 문제 
```
        7
      3   8
    8   1   0
  2   7   4   4
4   5   2   6   5
```

위 그림은 크기가 5인 정수 삼각형의 한 모습이다.

맨 위층 7부터 시작해서 아래에 있는 수 중 하나를 선택하여 아래층으로 내려올 때, 이제까지 선택된 수의 합이 최대가 되는 경로를 구하는 프로그램을 작성하라. 아래층에 있는 수는 현재 층에서 선택된 수의 대각선 왼쪽 또는 대각선 오른쪽에 있는 것 중에서만 선택할 수 있다.

삼각형의 크기는 1 이상 500 이하이다. 삼각형을 이루고 있는 각 수는 모두 정수이며, 범위는 0 이상 9999 이하이다.


### 입력
첫째 줄에 삼각형의 크기 n(1 ≤ n ≤ 500)이 주어지고, 둘째 줄부터 n+1번째 줄까지 정수 삼각형이 주어진다.


### 출력
**<u>첫째 줄에 합이 최대가 되는 경로에 있는 수의 합을 출력한다.</u>**


### 문제풀이
1. 배열로 입력값을 다 받는다.  
[7]  
[3,8]  
[8,1,0]  
[2,7,4,4]  
[4,5,2,6,5]

2. 위에서부터 대각선에 해당하는 값을 더해주면서 내려온다.  
```
[7] 			-> [7]  
[3, 8] 			-> [10(7+3), 15(7+8)]  
[8, 1, 0] 		-> [18(10+8), 16(15+1), 15(15+0)]  
[2, 7, 4, 4] 	-> [20(18+2), 25(18+7), 20(16+4), 19(15+4)]  
[4, 5, 2, 6, 5] -> [24(20+4), 30(25+5), 27(25+2), 26(20+6), 24(19+5)]  
```

대각선에 해당하는 값을 더해주면서 내려오는데, 두개의 대각선을 더할 수 있다면 그 값중 큰값을 더해주면서 내려온다.  


### 코드
```python
import sys

read = lambda: sys.stdin.readline().rstrip()

n = int(read())

triangle = []

for i in range(n):
    triangle.append(list(map(int, read().split())))

for i in range(1, n):
    for j in range(len(triangle[i])):
        if j == 0:
            triangle[i][j] += triangle[i-1][j]
        elif j == i:
            triangle[i][j] += triangle[i-1][j-1]
        else:
            triangle[i][j] += max(triangle[i-1][j], triangle[i-1][j-1])

print(max(triangle[n-1]))
```