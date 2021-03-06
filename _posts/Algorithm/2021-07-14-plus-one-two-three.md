---
layout: post
title: 백준 9095번 1, 2, 3 더하기 (python 파이썬)
subtitle: 백준 9095번 1, 2, 3 더하기
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 9095번 1, 2, 3 더하기 문제를 Python으로 해결한 문제이다.  

* [백준 9095번 1, 2, 3 더하기 문제 링크](https://www.acmicpc.net/problem/9095){:target="_blank"}


### 문제 
정수 4를 1, 2, 3의 합으로 나타내는 방법은 총 7가지가 있다. 합을 나타낼 때는 수를 1개 이상 사용해야 한다.

* 1+1+1+1
* 1+1+2
* 1+2+1
* 2+1+1
* 2+2
* 1+3
* 3+1

정수 n이 주어졌을 때, n을 1, 2, 3의 합으로 나타내는 방법의 수를 구하는 프로그램을 작성하시오.


### 입력
첫째 줄에 테스트 케이스의 개수 T가 주어진다. 각 테스트 케이스는 한 줄로 이루어져 있고, 정수 n이 주어진다. n은 양수이며 11보다 작다.


### 출력
**<u>각 테스트 케이스마다, n을 1, 2, 3의 합으로 나타내는 방법의 수를 출력한다.</u>**


### 문제풀이
해당 문제는 다음과 같은 규칙이 있다.  
1 = (1)  
2 = (1 + 1), (2)  
3 = (1 + 1 + 1), (1 + 2), (2 + 1), (3)  
4 = (1 + 1 + 1 + 1), (1 + 1 + 2), (1 + 2 + 1), (1 + 3), (2 + 1 + 1), (2 + 2), (3 + 1)

1. 4를 확인해보면 1에다가 3에서 더해졌던 숫자들이 더해지는것을 볼 수 있다.  
    * (1 + (1 + 1 + 1)), (1 + (1 + 2)), (1 + (2 + 1)), (1 + (3))

2. 그리고 2에다가 2에서 더해졌던 숫자들이 더해지는것을 볼 수 있다.  
    * (2 + (1 + 1)), (2 + (2))

3. 그리고 3에다가 1에서 더해졌던 숫자들이 더해지는것을 볼 수 있다.  
    * (3 + (1))   

결국 4는 1,2,3의 개수를 다 더한 값이 되는걸 볼 수 있다.  
그래서 규칙을 찾아보면 입력값의 -3, -2, -1의 값을 다 더하면 입력값의 개수가 된다.

### 코드
```python
import sys

read = lambda: sys.stdin.readline().rstrip()

dp = [1, 2, 4]

for i in range(3, 10):
    dp.append(dp[i-3] + dp[i-2] + dp[i-1])

T = int(read())
answer = []

for i in range(T):
    N = int(read())
    answer.append(dp[N-1])

print('\n'.join(map(str, answer)))
```