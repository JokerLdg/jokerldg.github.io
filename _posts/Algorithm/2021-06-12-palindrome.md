---
layout: post
title: 백준 17609번 회문 (python 파이썬)
subtitle: 백준 17609번 회문
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
백준 17609번 회문 문제를 Python으로 해결한 문제이다.  

* [백준 17609번 회문 문제 링크](https://www.acmicpc.net/problem/17609){:target="_blank"}


### 문제 
회문(回文) 또는 팰린드롬(palindrome)은 앞 뒤 방향으로 볼 때 같은 순서의 문자로 구성된 문자열을 말한다. 예를 들어 ‘abba’ ‘kayak’, ‘reviver’, ‘madam’은 모두 회문이다. 만일 그 자체는 회문이 아니지만 한 문자를 삭제하여 회문으로 만들 수 있는 문자열이라면 우리는 이런 문자열을 “유사회문”(pseudo palindrome)이라고 부른다. 예를 들어 ‘summuus’는 5번째나 혹은 6번째 문자 ‘u’를 제거하여 ‘summus’인 회문이 되므로 유사회문이다.

여러분은 제시된 문자열을 분석하여 그것이 그 자체로 회문인지, 또는 한 문자를 삭제하면 회문이 되는 “유사회문”인지, 아니면 회문이나 유사회문도 아닌 일반 문자열인지를 판단해야 한다. 만일 문자열 그 자체로 회문이면 0, 유사회문이면 1, 그 외는 2를 출력해야 한다. 


### 입력
입력의 첫 줄에는 주어지는 문자열의 개수를 나타내는 정수 T(1 ≤ T ≤ 30)가 주어진다. 다음 줄부터 T개의 줄에 걸쳐 한 줄에 하나의 문자열이 입력으로 주어진다. 주어지는 문자열의 길이는 3 이상 100,000 이하이고, 영문 알파벳 소문자로만 이루어져 있다.


### 출력
**<u>각 문자열이 회문인지, 유사 회문인지, 둘 모두 해당되지 않는지를 판단하여 회문이면 0, 유사 회문이면 1, 둘 모두 아니면 2를 순서대로 한 줄에 하나씩 출력한다.</u>**


### 문제풀이
1. 회문 판단은 슬라이싱을 이용하여 문자열을 뒤집어서 비교한다. 
    * 일치하면 회문이므로 바로 0을 리턴한다. 
2. ispalindrome함수에서는 left와 right의 문자가 같은지 비교하며 left를 1씩 증가시키고 right를 1씩 감소시켜
가운데로 이동한다.
3. while문을 이용하여 left가 right보다 작을 때까지 반복한다.
4. 반복문을 순회하면서 left와 right가 다른 문자가 있을 경우 유사회문인지 검사해야한다.
    * 유사회문은 1문자를 제외하고 회문인 경우므로, 다른 문자가 있을때 left를 한칸 건너 뛰고 검사하거나 right를 한칸 건너 뛰고 검사 했을 때 회문이 되면 된다.
    * 따라서 ispseudo함수에 각각 인자를 left+1, right-1로 변경하여 검사한다.
5. ispseudo함수에서도 다른 문자가 나올 경우 일반 문자열이고 다른 문자가 나오지 않을 경우 유사회문이다.

각각을 판단하여 return 해주면 모든 경우를 판단할 수 있다.


### 코드
```python
import sys

def ispseudo(word, left, right):
    while left < right:
        if word[left] == word[right]:
            left += 1
            right -= 1
        else:
            return False
    return True

def ispalindrome(word, left, right):
    if word == word[::-1]:
        return 0
    else:
        while left < right:
            if word[left] != word[right]:
                check_left = ispseudo(word, left + 1, right)
                check_right = ispseudo(word, left, right - 1)

                if check_left or check_right:
                    return 1
                else:
                    return 2
            else:
                left += 1
                right -= 1

T = int(sys.stdin.readline().rstrip("\n"))

for _ in range(T):
    word = sys.stdin.readline().rstrip("\n")
    left, right = 0, len(word)-1
    answer = ispalindrome(word, left, right)
    print(answer)
```