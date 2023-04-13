---
title:  "[OS] CPU Scheduling이란?"

categories:

- OS
  tags:
- [CPU Scheduling, OS]

toc: true
toc_sticky: true

date: 2022-12-26
last_modified_at: 2023-01-01
---

### 1. 정의

- 프로세스가 생성되어 실행될 때 필요한 시스템의 여러 자원을 해당 프로세스에게 할당하는 작업

### 2. 목적

- 공정한 스케줄링, 처리량의 극대화, 응답시간 최소화
- 균형있는 자원 사용, 실행의 무한 연기 배제, 반환시간 예측가능

### 3. 기준

- Utilization (CPU 이용률) : CPU를 이용한 수치의 백분율
- Throughtput : 단위 시간당 완료된 프로세스의 수
- Response Time : 작업 요청 후 응답이 오는데 걸리는 시간
- Waiting Time : 대기 큐에서의 대기 시간

### 4. 종류

| 구분 | 선점(Preemptive) | 비선점(Non-preempttive) |
|:---:|:---:|:---:|
| 개념 | P1이 CPU점유, P2가 CPU 점유 가능 | P1이 CPU 점유, P2는 대기 |
| 장점 | 빠른 응답, 시분할 시스템에 적합 | 응답시간 예상 가능, 공정한 처리 |
| 단점 | 오버헤드 발생 (Context Switching) | 짧은 작업도 긴 대기 발생 |

### 5. 알고리즘 종류

#### 1. 선점(Preemptive) 알고리즘

| 종류 | 주요 내용 |
|:---:|:---:|
| Round Robin | 같은 크기의 CPU를 할당하는 순환 할당 방식 <br> FCFS에 의해 프로세스가 CPU를 할당 받으면 Time Slicke에 의해 같은 시간의 CPU를 할당 <br> 시분할 방식에 효과적이며 할당시간(Time Slice)의 크기가 중요 <br> 할당 시간이 크면 FCFS에 가까워진다. |
| SRT | Short Remaining Time <br> 대기 큐의 가장 짧은 소요시간의 Process 선택 <br> 실행 중 선점가능 |
| Multi Level Queue | 작업을 그룹화하여 여러 큐 관리 및 할당 |
| Multi Level Feedback Queue | 여러 개의 큐를 두고 큐마다 다른 시간 할당량(Time Slice) 부여 <br> 짧은 작업 유리, 입출력 작업에 우선권 부여 <br> 하위 단계일수록 할당시간이 커짐 |

#### 2. 비선점(Non-Preemptive) 알고리즘

| 종류 | 주요 내용 |
|:---:|:---:|
| FCFS | First Come First Service <br> 도착한 순서대로 처리(일괄처리) |
| SJF | Shortest Job First <br> 준비 큐에서 가장 짧은 소요시간의 프로세스 실행 <br> FCFS보다 평균 대기 시간 감소 <br> 긴 프로세스가 짧은 프로세스에게 계속 작업 순위가 밀리게 되어 실행되지 못하은 기아현상(Starvation) 발생 |
| Priority | 프로세스에 우선순위 부여하여 우선순위에 따라 할당 <br> 정적 할당 : 실행 중 우선 순위를 바꾸지 않음 <br> 동적 할당 : 상황 변화에 적응하여 우선 순위의 변경이 가능 |
| Deadline | 작업을 명시된 시간이나 기한 내 완료하는 방식 |
| HRN | Highest Response Next <br> 긴 작업과 짧은 공정성을 고려한 방식 <br> Response Ratio가 높은 것을 선택 (Response Ratio = (대기시간 + 처리시간) / 처리시간) <br> SJF의 단점을 보완하여 Starvation 현상 방지 <br> 짧은 작업이나 대기 시간이 긴 작업은 우선 순위가 높아짐 |

###### Reference <br>

- https://zzsza.github.io/development/2018/07/29/cpu-scheduling-and-process/
- https://m.blog.naver.com/scw0531/221417295183
- https://com24everyday.tistory.com/168