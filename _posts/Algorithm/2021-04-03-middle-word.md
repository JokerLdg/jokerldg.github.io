---
layout: post
title: 프로그래머스 가운데 글자 가져오기 (python 파이썬)
subtitle: 프로그래머스 가운데 글자 가져오기
comments: true
categories: [Algorithm]
tags: [Algorithm]
sitemap :
changefreq : daily
priority : 1.0
---
프로그래머스 가운데 글자 가져오기 문제를 Python으로 해결한 문제이다.  

* [프로그래머스 가운데 글자 가져오기 문제 링크](https://programmers.co.kr/learn/courses/30/lessons/12903){:target="_blank"}

### 문제 
단어 s의 가운데 글자를 반환하는 함수, solution을 만들어 보세요. 단어의 길이가 짝수라면 가운데 두글자를 반환하면 됩니다.

### 제한사항
* s는 길이가 1 이상, 100이하인 스트링입니다.


### 입출력 예

|a|return|
|-----|-----|
|"abcde"|"c"|
|"qwer"|"we"|


### 문제풀이
* 배열을 2로 나눈 지점을 저장해준다.
* 짝수면 2로 나눈지점의 -1부터 나눈지점까지 출력한다.
* 홀수면 2로 나눈지점을 출력하면 된다.


### 코드
```python
def solution(s):
    answer = ''

    if len(s) % 2 == 0:
      point = len(s)//2
      answer = s[point-1:point+1]
    else:
      point = len(s)//2
      answer = s[point]

    return answer
```