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

- 공유된 자원에 여러 Process/Thread가 동시에 접근하면 Critical Section(임계 영역/) 문제가 발생하여 원하는 결과가 나오지 않을 수 이씨 때문에 한 번에 하나의 Process만 접근할 수
  있도록 제한을 둬야 한다.

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

![image](https://user-images.githubusercontent.com/61777583/212901173-f78926fd-7319-4dbd-b74c-412bc0e72fe9.png)

```
pthread_mutex_t mutex = PTHREAD_MUTEX_INITIALIZER;
...
do {
	pthread_mutex_lock(&mutex);
    ...
    //critical section
    ...
    pthread_mutex_unlock(&mutex);
}
```

### 5. Semaphore(세마포어)

- 한정된 자원을 여러 Thread가 사용하려고 할 때 접근을 제한한다.
- 다중 Thread 간 공유 자원 접근 순서를 제어하고 공유 자원의 수와 접근 스레드 수에 따라서 보다 유연하게 공유 영역으로의 접근을 제어한다.
- 커널에 저장된 변수 개념으로 두 가지 atomic 연산 P, V가 존재한다. P는 test를 의미, acquire() 기능이고 V는 increment, release() 기능이다.
- 프로세스가 임계영역 진입 시 P연산으로 세마포어의 값 감소
- 작업 수행 완료 후 임계영역 밖으로 나오면 V연산이 세마포어의 값 증가
- Busy-Wait 방식 : 루프(while)를 실행하여 접근 가능 체크
- Block-WakeUp 방식 : 요청 시 일단 자원 카운트 감소, 자원이 0 이하라면 대기 큐 삽입, 작업이 완료되어 카운트 증가시키며 반납해도 변수가 0 이하라면 대기 프로세스가 존재함을 의미하기에
  popleft 후 wakeup
- 임계 영역이 길면 Block-WakeUp 방식, 짧으면 Busy-Wait이 유리
- 카운팅 세마포어 : 임계영역 안에 프로세스/스레드 진입 시 카운트 증가시켜 일정 숫자 유지
- 이진 세마포어 0과 1로만 이루어진 세마포어로 임계 영역 안에 하나의 프로세스만 들어가게 함. 뮤텍스라고도 한다.
- 세마포어, 뮤텍스 차이점 : 뮤텍스는 동기화 대상이 1개, 세마포어는 1개 이상일 때 사용
- 세마포어에서도 데드락 발생 가능

![image](https://user-images.githubusercontent.com/61777583/212901253-3eba2486-699b-43d0-a694-6c8e99f44281.png)

```
sem_t semaphore;

sem_init(&semaphore, 0, 3); //3으로 초기화
...
do {
	sem_wait(&semaphore);
    ...
    //critical section
    ...
    sem_post(&semaphore);
}
```

### 6. Event(이벤트)

- 특정한 이벤트가 발생했음을 다른 Thread에게 알린다.
- Thread의 작업이 종료되면 신호 상태로 변경되고, 다른 Thread가 작업하도록 한다.

### 7. Waitable Timer

- 특정 시간이 지나면 대기 중인 Thread에게 알린다.
- 정해진 시간이 지나면 자동으로 신호 상태로 변경된다.

---

## 2. 교착상태

### 1. 정의

- 둘 이상의 Process들이 자원을 점유한 상태에서 서로 다른 프로세스가 점유하고 있는 자원을 요구하며 무한 대기를 하는 상태

### 2. 발생 조건

- 상호 배제 (Mutual Exclusion): 공유 자원은 한 번에 하나의 프로세스만 사용할 수 있음
- 점유 및 대기 (Hold and Wait): 프로세스가 공유 자원을 점유한 상태에서 다른 자원을 얻기 위해 대기하고 있는 상태여야 함
- 비선점 (No preemption): 프로세스가 한 자원을 점유하고 있으면 다른 프로세스가 강제로 빼앗을 수 없음
- 순환 대기 (Circular Wait): 프로세스의 집합에서 순환 형태로 자원을 대기하고 있어야 함

### 3. 해결 방법

- 교착 상태 예방
    - 교착상태 발생 조건 중 하나라도 발생하지 않게 하여 예방하는 방법
    - 조건 중 하나 이상을 부정하여 방지할 수 있다.
        - 상호배제 부정 : 읽기 전용 공유 자원을 사용한다.
        - 점유 및 대기 부정 : 프로세스가 실행되기 전 필요한 모든 자원을 할당(자원 낭비 발생)하거나 자원을 점유하고 있지 않을 때만 다른 자원을 요청할 수 있도록 한다.(기아 상태가 될 수 있다.)
        - 비선점 부정 : 모든 자원에 대해 선점을 허용한다 → 자원 낭비가 발생한다.
        - 순환 대기 부정 : 자원에 고유한 번호를 할당하고 번호 순서대로 자원을 요구하도록 한다.(자원 낭비 발생)
    - 시스템의 처리량이나 효율성을 떨어뜨리고 비현실적이다.

- 교착 상태 회피
    - 교착 상태가 발생하기 전에 안전한 상태에서만 자원 요청을 허용하는 방법
        - 안전 상태 (Safe state): 교착상태를 발생시키지 않고 자원을 할당하는 순서 (safe sequence)가 존재해서 모든 프로세스가 정상적으로 종료할 수 있는 상태
        - 불안전 상태 (Unsafe state): 교착상태가 발생할 수 있는 상태
    - 다음과 같은 가정이 필요하다.
        - Process 수가 고정되어 있어야 한다.
        - 자원의 종류와 수가 고정되어 있어야 한다.
        - Process가 요구하는 자원 및 최대 자원의 수를 알아야 한다.
        - Process는 반드시 자원을 사용 후 반납해야 한다.
    - 자원 할당 그래프 (Resourcec-Allocation Graph) 알고리즘
        - 자원 인스턴스 하나만 있는 경우 사용, 자원을 할당받을 때 그래프에 사이클이 생기면 요청을 거부하는 방식
    - 은행원 알고리즘
        - 자원 인스턴스가 여러개일 경우 사용
        - 자원 요청을 승인했을 때 안전한 상태가 유지되는 경우만 자원 할당
        - 불안전 상태가 예상되면 다른 프로세스가 끝날 때까지 대기

- 교착 상태 탐지
    - 탐지 알고리즘을 사용하여 교착 상태가 발생했는지 탐지한다.
    - 대기 그래프 알고리즘
        - 자원 할당 그래프를 변형해서 각 Process가 다른 Process가 보유하고 있는 자원을 기다리는 경우 간선을 추가하고, 사이클이 생기면 교착 상태를 탐지한다.
    - 은행원 알고리즘
        - 현재 상태가 안전 상태인지 확인하고, 불안전 상태면 교착상태라고 판단한다.
    - 탐지 알고리즘은 자원을 요청했으나 즉시 할당받지 못할 때, CPU 이용률이 특정 값 이하로 떨어질 때, 또는 주기적으로 일정 시간마다 호출을 해서 오버헤드를 최소한으로 한다.

- 교착 상태 복구
    - 교착 상태를 일으킨 Process를 종료하거나 할당된 자원을 해제시키는 방법
    - Process 종료
        - 교착 상태의 Process를 모두 중지 or 교착 상태가 풀릴 때까지 Process를 하나씩 중지
    - 자원 선점
        - 교착 상태에 있는 Process의 자원을 다른 Process에게 선점 할당해서 해당 Process를 정지시키는 방법
            - 최소의 피해를 줄 수 있는 Process를 선택한다.
            - 기아상태를 방지해야 한다.

## 3. 기아 상태 (Starvation)

- 특정 Process가 원하는 자원을 계속 할당 받지 못하는 상태
    - 여러 프로세스가 부족한 자원을 점유하기 위해 경쟁할 때 발생한다.
- 해결 방법
    - Process 우선 순위를 수시로 변경해서 모든 Process에게 기회를 준다.
    - 오래 기다린 Process의 우선 순위를 높인다.
    - 우선 순위가 아닌 요청을 순서대로 처리하는 큐를 사용한다.

(UI 정리 필요)

###### Reference

- https://mingmi-programming.tistory.com/79
- https://8iggy.tistory.com/184
- https://velog.io/@yun8565/%EB%8F%99%EA%B8%B0%ED%99%94%EC%99%80-%EA%B5%90%EC%B0%A9%EC%83%81%ED%83%9CDeadlock
- https://ooeunz.tistory.com/94