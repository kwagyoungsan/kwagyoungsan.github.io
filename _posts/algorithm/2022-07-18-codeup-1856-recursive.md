---
title:  "[Algorithm] 1851 : [기초-재귀함수] 재귀로 * n개 한 줄로 출력하기"

categories:

- CodeUp
  tags:
- [Algorithm, CodeUp, Recursion]

toc: true
toc_sticky: true

date: 2022-07-18
last_modified_at: 2022-07-18
---

## 문제 🔎

한 번에 계단을 1개 또는 2개 또는 3개를 뛰어 오를 수 있을 때,<br>
한 정수 n을 입력받아 바닥(0번째 계단)에서 n번째 계단까지 도착할 수 있는 방법의 가짓수를 출력하시오.<br>
(단, 반복문은 사용할 수 없다.)

예를 들어, <br>
1번째 계단에 도착하는 방법은 1가지 뿐이고,<br>
2번째 계단에 도착하는 방법은 2가지(1개-1개 뛰기, 2개 뛰기),<br>
3번째 계단에 도착하는 방법은 4가지(1개-1개-1개, 1개-2개, 2개-1개, 3개) 이다.

### 입력

int 형 정수(n) 1개가 입력된다.
(1 <= n <= 25)

### 출력

0 번째 계단에서 시작해서 한 번에 1개/2개/3개의 계단을 뛰어넘을 수 있을 때, n 번째 계단에 도착할 수 있는 방법의 가짓수를 출력한다.

### 입력 예시

3

### 출력 예시

5

## 풀이 🔎

```
n = int(input())

dic = {1:1, 2:2, 3:4}

def recur(num):
    if num in dic:
        return dic[num]

    else:
        dic[num]= recur(num - 3) + recur(num - 2) + recur(num - 1)
        
        return dic[num]
        
recur(n)
print(dic[n])

```