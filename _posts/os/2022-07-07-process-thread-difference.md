---
title:  "[OS] 프로세스(Process)와 스레드(Thread)의 차이점"

categories:

- OS
  tags:
- [Thread, Process, Multi Process, Multi Thread, Thread Safe, Context Switching, OS]

toc: true
toc_sticky: true

date: 2022-07-07
last_modified_at: 2022-09-13
---

## Process와 Thread의 예시🔎

내가 이해한 방법을 토대로 설명하도록 하겠다. 정확하지 않을 수 있으니 참고 바란다.<br>

- 프로세스 : 안드로이드 스튜디오, 크롬, 파일 탐색기, 카카오톡 등등
- 스레드 : 카카오톡을 실행하면서 <u>A에게 카톡을 보내는 스레드</u>와 <u>B에게 카톡이 오는 스레드</u>가 있다.<br><br>

---
<br>

## Process와 Thread의 차이점❗️

한 프로세스가 다른 프로세스의 자원에 접근하려면 통신을 이용해야한다.

- 파이프, 파일, 소켓 등
  스레드는 같은 프로세스 안에 있는 여러 스레드들은 같은 힙 공간을 공유한다. 반면에 프로세스는 다른 프로세스의 메모리에 직접 접근할 수 없다.
  프로세스 내에서 각각 <u>Stack</u>만 따로 할당받고 <u>Code, Data, Heap</u> 영역은 공유한다.

![Parameter](https://user-images.githubusercontent.com/61777583/177722805-fb54b110-bd0c-43fc-a46c-1eb82c60ea62.png)


---
<br>

⭐️ Process와 Thread에 대해 정리하다 보니 `Multi Process, Multi Thread, Thread Safe, Context Switching`이 자주 등장한다. 그래서 이것들도 같이 정리하려고
한다. <br><br>

---
<br>

### Multi Process 🔎

#### 1. 정의

- 두개 이상 다수의 프로세서(cpu)가 협력적으로 하나 이상의 작업을 동시에 처리하는 것이다. (병렬처리)
- 각 Process 간 메모리 구분이 필요하거나 독립된 주소 공간을 가져야 할 경우 사용한다.

#### 2. 장점

- 독립된 구조로 안전성이 높은 장점이 있다.
- 프로세스 중 하나에 문제가 생겨도 다른 프로세스에 영향을 주지 않아, 작업 속도가 느려지는 손해 정도는 생기지만 정지되거나 하는 문제는 발생하지 않는다.
- 여러개의 프로세스가 처리되어야 할 때 동일한 데이터를 사용하고, 이러한 데이터를 하나의 디스크에 두고 모든 프러세서(cpu)가 이를 공유하면 비용적으로 저렴하다.

#### 3. 단점

- 독립된 메모리 영역이기 때문에 작업량이 많을수록 (`Context Switching`이 자주 일어나서 주소 공간의 공유가 잦을 경우) 오버헤드가 발생하여 성능저하가 발생할 수 있다.
- `Context Switching` 과정에서 캐시 메모리 초기화 등 무거운 작업이 진행되고 시간이 소모되는 등 오버헤드가 발생한다.
    - ❗️`Context Switching`에 대해서는 하단에서 추가적으로 설명할 예정이다.❗️

<br>

---
<br>

### Multi Thread 🔎

#### 1. 정의

- 하나의 프로세스에 여러 스레드로 자원을 공유하며 작업을 나누어 수행하는 것이다.<br>
  ![image](https://user-images.githubusercontent.com/61777583/189837580-cffa960d-c288-4c46-a457-7d8384590387.png)

<br>

#### 2. 장점

- 시스템 자원소모 감소 (자원의 효율성 증대)
    - Process를 생성하여 자원을 할당하는 시스템 콜이 줄어 자원을 효율적으로 관리할 수 있다.
- 시스템 처리율 향상 (처리비용 감소)
    - Thread 간 데이터를 주고 받는 것이 간단해지고, 시스템 자원 소모가 줄어든다.
    - Thread 사이 작업량이 작이 `Context Switching`이 빠르다. (캐시 메모리를 비울 필요가 없다.)
- 간단한 통신 방법으로 프로그램 응답시간 단축
    - Thread는 Process 내 Stack 영역을 제외한 메모리 영역을 공유하기에 통신 비용이 적다.
    - Heap 영역을 공유하므로 데이터를 주고 받을 수 있다.

#### 3. 단점

- 자원을 공유하기에 동기화 문제가 발생할 수 있다. (병목현상, DeadLock 등)
- 주의 깊은 설계가 필요하고 디버깅이 어렵다. (불필요부분까지 동기화하면, 대기시간으로 인해 성능저하 발생)
- 하나의 Thread에 문제가 생기면 전체 Process가 영향을 받는다.
- 단일 Process 시스템의 경우 효과를 기대하기 어렵다.

<br>

---
<br>

### Thread Safe (스레드 안전) 🔎

#### 1. 정의

- Multi Thread Programming에서 일반적으로 어떤 함수나 변수, 혹은 객체가 여러 Thread로부터 동시에 접근이 이루어져도 프로그램의 실행에 문제가 없음을 뜻한다.
- 보다 엄밀하게는 하나의 함수가 어떤 Thread로부터 호출되어 실행 중일 때, 다른 Thread가 그 함수를 호출하여 동시에 함께 실행되더라도 각 Thread에서의 함수의 수행 결과가 올바로 나오는 것으로
  정의한다.

#### 2. Thread Safe를 지키기 위한 방법

1. . Re-entrancy (재진입성)

- 어떤 함수가 한 Thread에 의해 호출되어 실행 중일 때, 다른 Thread가 그 함수를 호출하더라도 그 결과가 각각에게 올바로 주어져야 한다.

2. Thread-local storage (스레드 지역 저장소)

- 공유 자원의 사용을 최대한 줄여 각각의 Thread에서만 접근 가능한 저장소들을 사용함으로써 동시 접근을 막는다.
- 이 방식은 동기화 방법과 관련되어 있고, 또한 공유상태를 피할 수 없을 때 사용하는 방식이다.

3. Mutual exclusion (상호 배제)

- 공유 자원을 꼭 사용해야 할 경우 해당 자원의 접근을 Semaphores 등의 락으로 통제한다.

4. Atomic operations (원자 연산)

- 공유 자원에 접근할 때 원자 연산을 이용하거나 '원자적'으로 정의된 접근 방법을 사용함으로써 상호 배제를 구현할 수 있다.

#### 3. Thread Safe인지 아닌지 알아내는 방법

- 보통 어떤 프로그램이 Thread Safe인지 아닌지 알아내는 것은 간단하지 않지만 다음을 참고할 수 있다.
    1. <u>전역 변수</u>나 <u>힙, 파일</u>과 같이 여러 Thread가 동시에 접근 가능한 자원을 사용하는지 여부
    2. Handle과 Pointer를 통한 데이터의 간접 접근 여부
    3. 부수 효과를 가져오는 코드가 있는지 여부

<br>

---

<br>

### Context Switching (문맥 교환) 🔎

#### 1. 정의

- 하나의 Process가 CPU를 사용 중인 상태에서 다른 Process가 CPU를 사용하도록 하기 위해, 이정의 Process의 상태(문맥)를 보관하고 새로운 Process의 상태를 적재하는 작업
    - 한 Process의 문맥은 그 Process의 PCB (Process Control Block)에 기록되어 있다.
- Multi Process 환경에서 CPU가 어떤 하나의 Process를 실행하고 있는 상태에서 인터럽트 요청에 의해 다음 우선 순위의 Process가 실행되어야 할 때, 기존의 Process의 상태 또는
  register 값(Context)을 저장하고 CPU가 다음 Process를 수행하도록 새로운 Process의 상태 또는 register 값(Context)을 교체하는 작업

#### 2. 진행

- Task의 대부분 정보는 Register에 저장되고, PCB로 관리되고 있다.
- 현재 실행하고 있는 Task의 PCB 정보를 저장하게 된다. (Process Stack, Ready Queue)
- 다음 실행할 Task의 PCB 정보를 읽어 Register에 적재하고 CPU가 이전에 진행했던 과정을 연속적으로 수행할 수 있다.

#### 3. PCB 구조

![image](https://user-images.githubusercontent.com/61777583/189849438-dd348d98-72b5-42dc-a2b5-909cef29db12.png) <br>

- Process State : 프로세스 상태 (Create, Ready, Running, Waiting, Terminated)
- Process Counter : 다음 실행할 명령어의 주소값
- Cpu Registers : Accumulator, index register, stack pointers, general purpose registers

#### 4. Process vs Thread

- Context Switching 비용은 Process가 Thread보다 많이 든다.
    1. Thread는 Stack 영역을 제외한 모든 메모리를 공유하기 때문이다.
    2. Context Switching 발생 시 Stack 영역만 변경을 진행하면 된다.
       <br>

#### Context란❓

- 사용자와 다른 사용자, 사용자와 시스템 또는 디바이스 간의 상호작용에 영향을 미치는 사람, 장소, 개체 등의 현재 상황(상태)을 규정하는 정보들
    - CPU가 해당 Process를 실행하기 위한 해당 Process의 정보들

###### Reference <br>

- https://wooody92.github.io/os/%EB%A9%80%ED%8B%B0-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%EC%99%80-%EB%A9%80%ED%8B%B0-%EC%8A%A4%EB%A0%88%EB%93%9C/
- https://gompangs.tistory.com/entry/OS-Thread-Safe%EB%9E%80
- https://jeong-pro.tistory.com/93
- https://nesoy.github.io/articles/2018-11/Context-Switching

[맨 위로 이동하기](#){: .btn .btn--primary }{: .align-right} 