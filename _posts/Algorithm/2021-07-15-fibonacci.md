---
layout: post
title: 백준 1003번 피보나치 함수 (python 파이썬)
subtitle: 백준 1003번 피보나치 함수
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 1003번 피보나치 함수 문제를 Python으로 해결한 문제이다.  

* [백준 1003번 피보나치 함수 문제 링크](https://www.acmicpc.net/problem/1003){:target="_blank"}


### 문제 
다음 소스는 N번째 피보나치 수를 구하는 C++ 함수이다.

```c++
int fibonacci(int n) {
    if (n == 0) {
        printf("0");
        return 0;
    } else if (n == 1) {
        printf("1");
        return 1;
    } else {
        return fibonacci(n‐1) + fibonacci(n‐2);
    }
}
```

fibonacci(3)을 호출하면 다음과 같은 일이 일어난다.

* fibonacci(3)은 fibonacci(2)와 fibonacci(1) (첫 번째 호출)을 호출한다.
* fibonacci(2)는 fibonacci(1) (두 번째 호출)과 fibonacci(0)을 호출한다.
* 두 번째 호출한 fibonacci(1)은 1을 출력하고 1을 리턴한다.
* fibonacci(0)은 0을 출력하고, 0을 리턴한다.
* fibonacci(2)는 fibonacci(1)과 fibonacci(0)의 결과를 얻고, 1을 리턴한다.
* 첫 번째 호출한 fibonacci(1)은 1을 출력하고, 1을 리턴한다.
* fibonacci(3)은 fibonacci(2)와 fibonacci(1)의 결과를 얻고, 2를 리턴한다.

1은 2번 출력되고, 0은 1번 출력된다. N이 주어졌을 때, fibonacci(N)을 호출했을 때, 0과 1이 각각 몇 번 출력되는지 구하는 프로그램을 작성하시오.


### 입력
첫째 줄에 테스트 케이스의 개수 T가 주어진다.

각 테스트 케이스는 한 줄로 이루어져 있고, N이 주어진다. N은 40보다 작거나 같은 자연수 또는 0이다.


### 출력
**<u>각 테스트 케이스마다 0이 출력되는 횟수와 1이 출력되는 횟수를 공백으로 구분해서 출력한다.</u>**


### 문제풀이
해당 문제에는 다음과 같은 규칙이 있다.

|N값|0|1|2|3|4|5|6|7|8|
|-----|-----|-----|-----|-----|-----|-----|-----|
|0 호출횟수|1|0|1|1|2|3|5|8|13|
|1 호출횟수|0|1|1|2|3|5|8|13|21|

자세히 살펴보면 2부터 호출횟수는 피보나치 수열과 동일하다.  
0의 호출횟수를 살펴보면 N-2 + N-1의 값과 같고,  
1의 호출횟수를 살펴봐도 N-2 + N-1의 값과 동일하다.

이 규칙을 통해 zero와 one배열에 N-1 + N-2의 값을 더하여 집어넣어주면 된다.

### 코드
```python
import sys

read = lambda: sys.stdin.readline().rstrip()

zero = [1, 0, 1]
one = [0, 1, 1]

def solution(number):
    length = len(zero)

    if length <= number:
        for i in range(length, number+1):
            zero.append(zero[i-1]+zero[i-2])
            one.append(one[i-1]+one[i-2])
    print(zero[number], one[number])

T = int(read())

for _ in range(T):
    num = int(read())
    solution(num)
```