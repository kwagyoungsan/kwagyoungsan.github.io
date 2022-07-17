---
title:  "[Algorithm] 1851 : [기초-재귀함수] 재귀로 * n개 한 줄로 출력하기" 

categories:
  - CodeUp
tags:
  - [Algorithm, CodeUp, Recursion]

toc: true
toc_sticky: true

date: 2022-07-14
last_modified_at: 2022-07-14
---

## 문제 🔎
한 정수 n을 입력받아 n개의 별(*)을 출력하시오.
(단, 반복문은 사용할 수 없다.)

### 입력
int 형 정수(n) 1개가 입력된다.
(1 <= n <= 100)

### 출력
n 개의 * 을 한 줄로 출력한다.

### 입력 예시
3

### 출력 예시
***

## 풀이 🔎
```
n = int(input())

def recur(num):
    if num==0:
        return 
    
    print('*', end = '')
    recur(num-1)
    
recur(n)

```