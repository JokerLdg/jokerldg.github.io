---
layout: post
title: 백준 9009번 피보나치 (python 파이썬)
subtitle: 백준 9009번 피보나치
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 9009번 피보나치 문제를 Python으로 해결한 문제이다.  

* [백준 9009번 피보나치 문제 링크](https://www.acmicpc.net/problem/9009){:target="_blank"}


### 문제 
피보나치 수 ƒK는 ƒK = ƒK-1 + ƒK-2로 정의되며 초기값은 ƒ0 = 0과 ƒ1 = 1 이다. 양의 정수는 하나 혹은 그 이상의 서로 다른 피보나치 수들의 합으로 나타낼 수 있다는 사실은 잘 알려져 있다. 

하나의 양의 정수에 대한 피보나치 수들의 합은 여러 가지 형태가 있다. 예를 들어 정수 100은 ƒ4 + ƒ6 + ƒ11 = 3 + 8 + 89 또는 ƒ1 + ƒ3 + ƒ6 + ƒ11 = 1 + 2 + 8 + 89, 또는 ƒ4 + ƒ6 + ƒ9 + ƒ10 = 3 + 8 + 34 + 55 등으로 나타낼 수 있다. 이 문제는 하나의 양의 정수를 최소 개수의 서로 다른 피보나치 수들의 합으로 나타내는 것이다. 

하나의 양의 정수가 주어질 때, 피보나치 수들의 합이 주어진 정수와 같게 되는 최소 개수의 서로 다른 피보나치 수들을 구하라. 


### 입력
입력 데이터는 표준입력을 사용한다. 입력은 T 개의 테스트 데이터로 구성된다. 입력의 첫 번째 줄에는 테스트 데이터의 수를 나타내는 정수 T 가 주어진다. 각 테스트 데이터에는 하나의 정수 n이 주어진다. 단, 1 ≤ n ≤ 1,000,000,000. 


### 출력
**<u>출력은 표준출력을 사용한다. 하나의 테스트 데이터에 대한 해를 하나의 줄에 출력한다. 각 테스트 데이터에 대해, 피보나치 수들의 합이 주어진 정수에 대해 같게 되는 최소수의 피보나치 수들을 증가하는 순서로 출력한다. </u>**


### 문제풀이
1. 문제에 나온 최대값의 조건인 1,000,000,000의 값보다 큰수의 바로 아래까지 배열에 추가한다.
2. 피보나치 배열을 for문으로 탐색을 하는데 큰수부터 넣어야 하기 때문에 뒤에서부터 탐색한다.
3. 그리고 n이 피보나치의 수보다 크거나 같으면 answer에 넣어주고, n이 0이되면 종료한다.
4. answer 배열이 큰 값부터 들어가 있기 때문에 오름차순으로 정렬후 출력한다.


### 코드
```python
import sys

read = sys.stdin.readline

T = int(read())

fibonacci = [1, 2]

for i in range(2, 43):
    fibonacci.append(fibonacci[i-2] + fibonacci[i-1])

for _ in range(T):
    n = int(read())
    answer = []

    for f in fibonacci[::-1]:
        if n == 0:
            break

        if n >= f:
            n -= f
            answer.append(f)

    answer.sort()
    print(' '.join(map(str, answer)))
```