---
layout: post
title: 백준 1744번 수 묶기 (python 파이썬)
subtitle: 백준 1744번 문제 수 묶기
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 1744번 수 묶기 문제를 Python으로 해결한 문제이다.  

* [백준 1744번 수 묶기 문제 링크](https://www.acmicpc.net/problem/1744){:target="_blank"}

### 문제 
길이가 N인 수열이 주어졌을 때, 그 수열의 합을 구하려고 한다. 하지만, 그냥 그 수열의 합을 모두 더해서 구하는 것이 아니라, 수열의 두 수를 묶으려고 한다. 어떤 수를 묶으려고 할 때, 위치에 상관없이 묶을 수 있다. 하지만, 같은 위치에 있는 수(자기 자신)를 묶는 것은 불가능하다. 그리고 어떤 수를 묶게 되면, 수열의 합을 구할 때 묶은 수는 서로 곱한 후에 더한다.

예를 들면, 어떤 수열이 {0, 1, 2, 4, 3, 5}일 때, 그냥 이 수열의 합을 구하면 0+1+2+4+3+5 = 15이다. 하지만, 2와 3을 묶고, 4와 5를 묶게 되면, 0+1+(2*3)+(4*5) = 27이 되어 최대가 된다.

수열의 모든 수는 단 한번만 묶거나, 아니면 묶지 않아야한다.

**<u>수열이 주어졌을 때, 수열의 각 수를 적절히 묶었을 때, 그 합이 최대가 되게 하는 프로그램을 작성하시오.</u>**

### 입력
첫째 줄에 수열의 크기 N이 주어진다. N은 10,000보다 작은 자연수이다. 둘째 줄부터 N개의 줄에, 수열의 각 수가 주어진다. 수열의 수는 -10,000보다 크거나 같고, 10,000보다 작거나 같은 정수이다.

### 출력
**<u>수를 합이 최대가 나오게 묶었을 때 합을 출력한다. 정답은 항상 2^31보다 작다.</u>**

### 문제풀이
이 문제는 수열이 주어졌을 때, 수열의 각 수를 적절히 묶고 그 합이 최대가 되게 한 뒤 출력하는 문제이다.


**<u>접근방법</u>**  
해당 문제는 수 묶기의 규칙을 찾는 것이 중요한 문제이다.

찾은 규칙은 다음과 같다.

0, 양수 = 덧셈  
0, 음수 = 곱셈  

1, 양수 = 덧셈  
1, 음수 = 덧셈  
**즉, 1 = 덧셈**

양수, 양수 = 곱셈  
음수, 음수 = 곱셈  
양수, 음수 = 덧셈

양수 리스트는 내림차순 정렬, 음수 리스트는 오름차순 정렬을 해준다.  
해당 리스트의 길이가 짝수이면 리스트의 숫자를 2개씩 곱해주면 최댓값이 나온다.  
홀수이면 마지막 숫자를 빼고 2개씩 곱해주고 마지막 수를 더해준다.  

1 같은 경우 곱셈을 하면 최댓값이 안나오기 때문에 값에 그냥 1을 더해준다.

### 코드
```python
import sys
input = sys.stdin.readline

N = int(input())
positive  = [] # 양수를 저장할 리스트
negative = [] # 음수를 저장할 리스트
max_sum = 0

for _ in range(N):
  n = int(input())
  
  if n > 1:
    positive.append(n)
  elif n == 1:
    max_sum += 1 # 1, 양수의 규칙에 의해 1을 더한다.
  else:
    negative.append(n)

positive.sort(reverse=True) # 양수의 큰 수부터 정렬한다.
negative.sort() # 음수의 작은 수부터 정렬한다.

# 양수 리스트 더해주기
if len(positive) % 2 == 0: # 양수가 짝수개 일경우 두개씩 곱해준다.
  for i in range(0, len(positive), 2):
    max_sum += positive[i] * positive[i+1]
else:
  for i in range(0, len(positive)-1, 2): 
    max_sum += positive[i] * positive[i+1]
  max_sum += positive[len(positive)-1] # 마지막 수는 더해준다.

# 음수 더해주기
if len(negative) % 2 == 0: # 음수가 짝수개 일경우 두개씩 곱해준다.
  for i in range(0, len(negative), 2):
    max_sum += negative[i] * negative[i+1]
else:
  for i in range(0, len(negative)-1, 2):
    max_sum += negative[i] * negative[i+1]
  max_sum += negative[len(negative)-1] # 마지막 수는 더해준다.

print(max_sum)
```