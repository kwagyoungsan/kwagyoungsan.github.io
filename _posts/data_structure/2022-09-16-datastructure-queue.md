---
title:  "[Data Sturcture] 큐(Queue)에 대해 알아보자❗️"

categories:

- Data Structure
  tags:
- [Queue, Data Structure]

toc: true
toc_sticky: true

date: 2022-09-16
last_modified_at: 2022-10-03
---

## 큐(Queue)란? 🔎

### 1. 정의 🔎

- FIFO (First In First Out) 구조
    - 스택(Stack)과 반대의 개념

![image](https://user-images.githubusercontent.com/61777583/193552597-cecdea00-cb8f-417e-afc0-ed60f87bde58.png)

- 큐에 끝(Rear)에서 요소를 추가하는 작업 : enqueue
- 큐에 맨 앞(Front)에서 요소를 제거하는 작업 : dequeue

<br>

---

<br>

### 2. 기본 동작 🔎

1. enqueue() : 큐에 끝(rear)에 항목을 추가
2. dequeue() : 큐에 맨 앞(front)에 항목을 제거
3. peek() : 큐에 맨 앞(front)에 있는 항목을 반환
4. isfull() : 큐가 가득 찼는지 확인
5. isempty() : 큐가 비어 있는지 확인

<br>

---

<br>

### 3. 알고리즘 🔎

- 큐 생성

```java
createQueue()
        Q[n];
        front ← -1;
        rear ← -1;
        end createQueue()
```

- 새로 생성하여 저장된 원소가 없는 공백 큐이므로 front와 rear는 -1로 초기화합니다.

<br>

- 공백 상태 검사

```java
isEmpty(Q)
        if(front=rear)then return true;
        else return false;
        end isEmpty()
```

- 큐가 공백인 경우는 처음 공백 큐를 생성하여 front와 rear 값이 -1인 경우와 마지막에 삽입한 rear의 원소를 삭제하여 front가 rear의 위치에 있는 경우입니다. 따라서 front와 rear의 값이
  같을 때 큐는 공백 상태입니다.

<br>

- 포화 상태 검사

```java
isFull(Q)
        if(rear=n-1)then return true;
        else return false;
        end isFull()
```

- 큐가 포화 상태인 경우는 배열의 마지막 인덱스까지 원소가 저장된 경우이므로 rear의 값이 배열의 마지막 인덱스 n - 1과 값이 같을 때 큐는 포화 상태입니다.

<br>

- 삽입 연산(enQueue)

```jave
enQueue(Q, data)
    if(isFull(Q))    then Queue_Full();
    else{
        rear ← rear + 1;
        Q[rear] ← data;
    }
end enQueue()
```

- 포화 상태가 아닌 큐에 원소를 삽입하려면 배열에 저장되어 있는 마지막 원소의 다음 자리에 삽입해야 하므로 rear의 값을 하나 증가시키고 삽입합니다.

<br>

- 삭제 연산(deQueue)

```
dnQueue(Q)
    if(isEmpty(Q)) then Queue_Empty();
    else{
        front ← front + 1;
        return Q[front];
    }
end enQueue()
```

- 공백 상태가 아닌 큐에서 원소의 삭제는 큐에 저장된 원소 중에서 가장 먼저 삽입된 원소를 가장 먼저 삭제해야 합니다. 따라서 front의 값을 하나 증가시키고 원소를 삭제하여 반환합니다.

<br>

---

<br>

### 4. 큐를 구현하는 두가지 방법 🔎

1. Array 사용 <br>
   장점 : 구현하기 쉬움. <br>
   단점 : 크기가 동적이 아님. 런타임 시 필요에 따라 늘어나거나 줄어들지 않음.

2. Linked List 사용 <br>
   장점 : 크기가 동적임. 런타임시 필요에 따라 크기가 확장 및 축소될 수 있음. <br>
   단점 : 포인터를 위한 추가 메모리 공간이 필요함.

<br>

---

<br>

### 5. 큐의 종류 🔎

1. 선형 큐 (Linear Queue) <br>
   기본적인 큐의 형태로써 막대 모양으로 된 큐이다. <br>
   배열로 구현 시 크기가 제한되어 있고 빈 공간을 사용하려면 모든 자료를 꺼내거나 자료를 한 칸씩 옮겨야 한다는 단점이 있고 많은 수의 enqueue 및 dequeue 작업이 있는 경우 어느 시점에서 큐가
   비어있어도 자료를 삽입하지 못하는 경우가 발생한다.

2. 환형 큐 (Circular Queue) <br>
   선형 큐의 문제점을 보완한 것이 환형 큐이다. <br>
   환형 큐는 1차원 배열 형태의 큐를 원형(Circular)으로 구성하여 배열의 처음과 끝을 연결하여 만든다.
   원형 큐라고도 한다.

### 6. 큐의 사용 사례 🔎

1. 어떠한 작업/데이터를 순서대로 실행/사용하기 위해 대기시킬 때 사용한다. <br>
   ex) CPU 스케줄링, 디스크 스케줄링
2. 서로 다른 쓰레드 또는 프로세스 사이에서 자료를 주고 받을 때 자료를 일시적으로 저장하는 용도로 많이 사용한다. (비동기 전송)
   ex) I/O 버퍼, 파이프, 파일 I/O

<br>

---

<br>

###### Reference

- https://leejinseop.tistory.com/m/36
- https://velog.io/@kang9366/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%ED%81%90Queue

[맨 위로 이동하기](#){: .btn .btn--primary }{: .align-right} 