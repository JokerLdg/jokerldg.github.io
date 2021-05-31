---
layout: post
title: 프로그래머스 괄호 회전하기 (python 파이썬)
subtitle: 프로그래머스 괄호 회전하기
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 괄호 회전하기 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 괄호 회전하기 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/76502){:target="_blank"}


### 문제 설명
다음 규칙을 지키는 문자열을 올바른 괄호 문자열이라고 정의합니다.

* ```()```, ```[]```, ```{}``` 는 모두 올바른 괄호 문자열입니다.
* 만약 ```A```가 올바른 괄호 문자열이라면, ```(A)```, ```[A]```, ```{A}``` 도 올바른 괄호 문자열입니다. 예를 들어, ```[]``` 가 올바른 괄호 문자열이므로, ```([])``` 도 올바른 괄호 문자열입니다.
* 만약 ```A```, ```B```가 올바른 괄호 문자열이라면, ```AB``` 도 올바른 괄호 문자열입니다. 예를 들어, ```{}``` 와 ```([])``` 가 올바른 괄호 문자열이므로, ```{}([])``` 도 올바른 괄호 문자열입니다.

대괄호, 중괄호, 그리고 소괄호로 이루어진 문자열 ```s```가 매개변수로 주어집니다. 이 ```s```를 왼쪽으로 x (0 ≤ x < (```s```의 길이)) 칸만큼 회전시켰을 때 ```s```가 올바른 괄호 문자열이 되게 하는 x의 개수를 return 하도록 solution 함수를 완성해주세요.


### 제한 사항
* s의 길이는 1 이상 1,000 이하입니다.


### 입출력 예

|s|result|
|-----|-----|
|"[](){}"|3|
|"}]()[{"|2|
|"[)(]"|0|
|"}}}"|0|

### 입출력 예 설명
**예제 #1**  
* 다음 표는 "[](){}" 를 회전시킨 모습을 나타낸 것입니다.

|x|s를 왼쪽으로 x칸만큼 회전|올바른 괄호 문자열?|
|-----|-----|-----|
|0|"[](){}"|O|
|1|"](){}["|X|
|2|"(){}[]"|O|
|3|"){}[]("|X|
|4|"{}[]()"|O|
|5|"}[](){"|X|

* 올바른 괄호 문자열이 되는 x가 3개이므로, 3을 return 해야 합니다.


**예제 #2**  
* 다음 표는 "}]()[{" 를 회전시킨 모습을 나타낸 것입니다.

|x|s를 왼쪽으로 x칸만큼 회전|올바른 괄호 문자열?|
|-----|-----|-----|
|0|"}]()[{"|X|
|1|"]()[{}"|X|
|2|"()[{}]"|O|
|3|")[{}]("|X|
|4|"[{}]()"|O|
|5|"{}]()["|X|

* 올바른 괄호 문자열이 되는 x가 2개이므로, 2를 return 해야 합니다.


**예제 #3**
* s를 어떻게 회전하더라도 올바른 괄호 문자열을 만들 수 없으므로, 0을 return 해야 합니다.


**예제 #4**
* s를 어떻게 회전하더라도 올바른 괄호 문자열을 만들 수 없으므로, 0을 return 해야 합니다.


### 문제풀이
스택을 이용하여 푼 문제이다.

1. 문자열을 deque로 만들어서 isbracket 함수를 호출한다.
    * rotate 함수는 리스트의 내용을 음수는 왼쪽으로 양수는 오른쪽으로 회전하는 함수이다.
2. 문자열에 여는 괄호가 있으면 스택에 넣어준다.
3. 닫는 괄호일경우 스택이 있을경우 비교한다.
    * 스택에 없으면 적합한 괄호가 아니므로 False를 return
4. 1 ~ 3을 반복하여 stack에 데이터가 없으면 True, 아니면 False를 return한다.


### 코드
```python
from collections import deque

def ispair(open, close):
    if open == '[' and close == ']':
        return True
    elif open == '(' and close == ')':
        return True
    elif open == '{' and close == '}':
        return True
    else:
        return False

def isbracket(bracket):
    stack = []

    for b in bracket:
        if b in ('[', '(', '{'):
            stack.append(b)
        else:
            if not stack:
                return False
            else:
                open = stack.pop()
                close = b

                if not ispair(open, close):
                    return False

    return True if not stack else False

def solution(s):
    answer = 0

    for i in range(len(s)):
        bracket = deque(s)
        bracket.rotate(-i)

        if isbracket(bracket):
            answer += 1

    return answer
```
