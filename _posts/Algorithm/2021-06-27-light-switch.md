---
layout: post
title: 백준 2138번 전구와 스위치 (python 파이썬)
subtitle: 백준 2138번 전구와 스위치
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 2138번 전구와 스위치 문제를 Python으로 해결한 문제이다.  

* [백준 2138번 전구와 스위치 문제 링크](https://www.acmicpc.net/problem/2138){:target="_blank"}


### 문제 
N개의 스위치와 N개의 전구가 있다. 각각의 전구는 켜져 있는(1) 상태와 꺼져 있는 (0) 상태 중 하나의 상태를 가진다. i(1 < i < N)번 스위치를 누르면 i-1, i, i+1의 세 개의 전구의 상태가 바뀐다. 즉, 꺼져 있는 전구는 켜지고, 켜져 있는 전구는 꺼지게 된다. 1번 스위치를 눌렀을 경우에는 1, 2번 전구의 상태가 바뀌고, N번 스위치를 눌렀을 경우에는 N-1, N번 전구의 상태가 바뀐다.

N개의 전구들의 현재 상태와 우리가 만들고자 하는 상태가 주어졌을 때, 그 상태를 만들기 위해 스위치를 최소 몇 번 누르면 되는지 알아내는 프로그램을 작성하시오.


### 입력
첫째 줄에 자연수 N(2≤N≤100,000)이 주어진다. 다음 줄에는 전구들의 현재 상태를 나타내는 숫자 N개가 공백 없이 주어진다. 그 다음 줄에는 우리가 만들고자 하는 전구들의 상태를 나타내는 숫자 N개가 공백 없이 주어진다.


### 출력
**<u>첫째 줄에 답을 출력한다. 불가능한 경우에는 -1을 출력한다.</u>**


### 문제풀이
* 첫번째 전구를 키는 케이스와 키지 않는 케이스로 나눈다.
* 한 번 지나간 전구는 다시 건드리지 않는 것.
* 전구의 상태를 바꾸면 양 옆 전구가 바뀌기 때문에 두번째 전구부터 시작해서 이전 전구의 상태가 희망하는 상태와 같은지 확인하고 다르다면 스위치를 눌러 상태를 변경하는 것.

스위치를 누르면 한칸 앞의 전구와 자기자신과 다음 칸의 전구의 상태가 변한다.  

스위치를 누르는 횟수를 최소로 만들기 위해 누르는 스위치의 선택을 맨 앞에서 맨 끝까지 한번 검사하면 된다.  
누를지 말지 검사하는 기준은 맨 앞에서 맨 끝까지 한번 검사하기 때문에 한칸 앞의 전구 상태를 비교하여 같으면 누르지 않고 다르면 누르면 된다.

문제를 해결하기 위해 우선 맨 처음 스위치를 누를지 말지 경우를 나눠야 한다.

### 코드
```python
import sys

read = sys.stdin.readline

def change_zero(light):
    count = 1
    light[0] = not light[0]
    light[1] = not light[1]

    for i in range(1, len(light)):
        if light[i-1] == hope[i-1]:
            continue
        else:
            count += 1

            light[i-1] = not light[i-1]
            light[i] = not light[i]

            if i < len(light)-1:
                light[i+1] = not light[i+1]

    if hope == light:
        return count
    return 200002

def non_change_zero(light):
    count = 0

    for i in range(1, len(light)):
        if light[i-1] == hope[i-1]:
            continue
        else:
            count += 1

            light[i-1] = not light[i-1]
            light[i] = not light[i]

            if i < len(light)-1:
                light[i+1] = not light[i+1]

    if hope == light:
        return count

    return 100002

N = int(read().rstrip("\n"))

state = list(map(int, read().rstrip("\n")))
hope = list(map(int, read().rstrip("\n")))

count1 = change_zero(state[:])
count2 = non_change_zero(state[:])

answer = min(count1, count2)

if answer == 100002:
    answer = -1

print(answer)
```