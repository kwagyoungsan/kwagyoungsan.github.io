---
title:  "[OS] Synchonize & Deadlock?" 

categories:
  - OS
tags:
  - [Synchonize, Deadlock, OS]

toc: true
toc_sticky: true

date: 2022-12-26
last_modified_at: 2023-01-01
---

## 1. 동기화

### 1. 정의
- 시스템을 동시에 작동시키기 위해 여러 사건들을 조화시키는 것
- Process or Thread가 수행된느 시점을 조절하여 서로가 알고 있는 정보가 일치하는 것

### 2. 특징
- 공유된 자원에 여러 Process/Thread가 동시에 접근하면 Critical Section(임계 영역/) 문제가 발생하여 원하는 결과가 나오지 않을 수 이씨 때문에 한 번에 하나의 Process만 접근할 수 있도록 제한을 둬야 한다. 

### 3. Critical Section(임계 영역)
- 공유되는 자원에서 문제가 발생하지 않도록 독점을 보장해주는 영역
- Multi-Thread 프로그램에서 공유 자원이 참조 가능한 코드 영역
- 한 순간에 반드시 하나의 Process or Thread만 진입이 가능하다.
- 공유 자원 독점을 통해 동기화를 유지할 수 있다.
- 해결 조건
  - Mutual Exclusion(상호 배제)
    - 누군가 Critical Section에 들어가면 다른 이는 접근 불가
  - Progress(진행)
    - Critical Section에 작업 종료 Process/Thread가 없다면 진입하고자 하는 Process/Thread를 적절히 선택
  - Bounded Waiting(유한 대기)
    - 기아 상태 방지 위해 접근했을 경우 다음 진입 시 제한
- 소프트웨어 기반 동기화
  - 피터슨 알고리즘 / 데커 알고리즘
    - Process가 2개일 때만 사용 가능, busy-wait 문제 발생 가능 (루프 비용)
  - 램포트의 빵집 알고리즘
    - Process가 2개 이상일 경우에 사용 가능
- 하드웨어 기반 동기화

### 4. Mutex(뮤텍스)
- Critical Section과 마찬가지로 공유 자원에 여러 Thread가 접근하려고 할 때, Lock을 이용해 한 번에 하나의 Thread만 접근하도록 허용하는 것
- Critical Section은 한 Process 내의 Thread에만 사용 가능하지만, Mutex는 서로 다른 Process에 속한 Thread에도 적용 가능하다.

### 5. Semaphore(세마포어)
- 한정된 자원을 여러 Thread가 사용하려고 할 때 접근을 제한한다.
- 다중 Thread 간 공유 자원 접근 순서를 제어하고 공유 자원의 수와 접근 스레드 수에 따라서 보다 유연하게 공유 영역으로의 접근을 제어한다.

### 6.











###### Reference
- https://mingmi-programming.tistory.com/79
- https://8iggy.tistory.com/184
- https://velog.io/@yun8565/%EB%8F%99%EA%B8%B0%ED%99%94%EC%99%80-%EA%B5%90%EC%B0%A9%EC%83%81%ED%83%9CDeadlock
- https://ooeunz.tistory.com/94