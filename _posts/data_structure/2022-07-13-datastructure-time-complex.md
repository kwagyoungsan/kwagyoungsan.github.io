---
title:  "[Data Sturcture] 시간 복잡도에 대해 알아보자 !" 

categories:
  - Data Structure
tags:
  - [Time Complex, Data Structure]

toc: true
toc_sticky: true

date: 2022-07-13
last_modified_at: 2022-07-13
---

## 시간 복잡도

### 시간 복잡도란?  🔎
- (계산 복잡도 이론에서) 문제를 해결하는데 걸리는 시간과 입력의 함수 관계
* (알고리즘에서) 입력을 나타내는 문자열 길이의 함수로서 작동하는 알고리즘을 취해 시간을 정량화하는 것
    * 알고리즘의 시간 복잡도는 주로 Big-O 표기법을 사용.
        * Big-O : 계수과 낮은 차수의 항을 제외시키는 방법

***

### 표기방법 ❗️
- Big-O(빅-오) : 상한 점근
    - O(f(n)) : 아무리 느려도 f(n)정도이다. f(n)보다 빠르거나 같다.
- Big-Ω(빅-오메가) : 하한 점근
    - Ω(f(n)) : 아무리 빨라도 f(n)정도이다. f(n)보다 느리거나 같다.
- Big-θ(빅-세타) : 그 둘의 평균
    - θ(f(n)) : 상한과 하한을 함께 제시한다. 두 집합의 교집합
위의 세 가지 표기법은 시간 복잡도를 각각 최악, 최선, 중간(평균)의 경우에 대하여 나타내는 방법이다.

(점근 : 점점 가까워짐)

***

### 가장 자주 사용되는 표기법은? 🔎
- Big-O 표기법은 최악의 경우를 고려하므로, 프로그램이 실행되는 과정에서 소요되는 최악의 시간까지 고려할 수 있기 때문이다.
- ‘최소한 ~이 걸린다’, ‘~ 정도 시간이 걸린다’보다 ‘~정도 시간까지 걸릴 수 있다를 고려해야 그에 맞는 대응이 가능하다.

***

### Big-O 표기법의 종류 ❗️
1. O(1)
2. O(n)
3. O(log n)
4. O(n<sup>2)
5. O(2<sup>n)

https://hanamon.kr/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-time-complexity-%EC%8B%9C%EA%B0%84-%EB%B3%B5%EC%9E%A1%EB%8F%84/

###### 출처
- https://nolzaheo.tistory.com/3
- https://hanamon.kr/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-time-complexity-%EC%8B%9C%EA%B0%84-%EB%B3%B5%EC%9E%A1%EB%8F%84/
- 
