---
layout: post
title: 프로그래머스 다리를 지나는 트럭 (python 파이썬)
subtitle: 프로그래머스 다리를 지나는 트럭
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 다리를 지나는 트럭 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 다리를 지나는 트럭 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/42583){:target="_blank"}


### 문제 
트럭 여러 대가 강을 가로지르는 일 차선 다리를 정해진 순으로 건너려 합니다. 모든 트럭이 다리를 건너려면 최소 몇 초가 걸리는지 알아내야 합니다. 트럭은 1초에 1만큼 움직이며, 다리 길이는 bridge_length이고 다리는 무게 weight까지 견딥니다.
※ 트럭이 다리에 완전히 오르지 않은 경우, 이 트럭의 무게는 고려하지 않습니다.

예를 들어, 길이가 2이고 10kg 무게를 견디는 다리가 있습니다. 무게가 [7, 4, 5, 6]kg인 트럭이 순서대로 최단 시간 안에 다리를 건너려면 다음과 같이 건너야 합니다.

|경과 시간|다리를 지난 트럭|다리를 건너는 트럭|대기 트럭|
|-----|-----|-----|-----|
|0|[]|[]|[7,4,5,6]|
|1~2|[]|[7]|[4,5,6]|
|3|[7]|[4]|[5,6]|
|4|[7]|[4,5]|[6]|
|5|[7,4]|[5]|[6]|
|6~7|[7,4,5]|[6]|[]|
|8|[7,4,5,6]|[]|[]|

따라서, 모든 트럭이 다리를 지나려면 최소 8초가 걸립니다.

solution 함수의 매개변수로 다리 길이 bridge_length, 다리가 견딜 수 있는 무게 weight, 트럭별 무게 truck_weights가 주어집니다. 이때 모든 트럭이 다리를 건너려면 최소 몇 초가 걸리는지 return 하도록 solution 함수를 완성하세요.


### 제한사항
* bridge_length는 1 이상 10,000 이하입니다.
* weight는 1 이상 10,000 이하입니다.
* truck_weights의 길이는 1 이상 10,000 이하입니다.
* 모든 트럭의 무게는 1 이상 weight 이하입니다.


### 입출력 예

|bridge_length|weight|truck_weights|return|
|-----|-----|-----|-----|
|2|10|[7,4,5,6]|8|
|100|100|[10]|101|
|100|100|[10,10,10,10,10,10,10,10,10,10]|110|


### 문제풀이
* 해당 문제는 deque를 이용하여 풀어보았다.
* deque에서 차례대로 꺼내어 현재 무게에서 꺼낸값을 빼준다
* 현재 무게와 트럭의 첫번째 값을 더하여 다리 무게와 비교한다.
    * 현재 무게 + 트럭의 첫번째 값이 더 크면 다리 무게가 버틸수 없기 때문에 0을 넣는다.
    * 아니면 트럭의 무게에서 첫번째 값을 꺼내어 다리에 올리고 현재 무게를 트럭 무게만큼 더해준다.

### 코드
```python
from collections import deque

def solution(bridge_length, weight, truck_weights):
    answer = 0
    bridge_on = deque([0] * bridge_length)
    current_weight = 0

    while truck_weights:
        answer += 1
        bridge_out = bridge_on.popleft()
        current_weight -= bridge_out

        if current_weight + truck_weights[0] > weight:
            bridge_on.append(0)
        else:
            truck = truck_weights.pop(0)
            bridge_on.append(truck)
            current_weight += truck

    while current_weight > 0:
        answer += 1
        bridge_out = bridge_on.popleft()
        current_weight -= bridge_out

    return answer
```
