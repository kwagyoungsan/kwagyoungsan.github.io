---
title:  "[Data Sturcture] 연결 리스트(Linked List)에 대해 알아보자❗️"

categories:

- Data Structure
  tags:
- [Linked List, Data Structure]

toc: true
toc_sticky: true

date: 2022-09-14
last_modified_at: 2022-09-14
---

## 연결 리스트(Linked List)란? 🔎

### 1. 정의 🔎

- 각 노드가 데이터와 포인터를 가지고 한 줄로 연결되어 있는 방식으로 데이터를 저장하는 자료 구조
- 이름에서 말하듯이 데이터를 담고 있는 노드들이 연결되어 있는데, 노드의 포인터가 다음이나 이전의 노드와의 연결을 담당하게 된다.
  <br>

---

<br>

### 2. 종류 🔎

#### 1. 단일 연결 리스트 <br>

![image](https://user-images.githubusercontent.com/61777583/190062524-9ef353f9-89fe-41a6-a658-0277ed5d1ecf.png)

- 각 노드에 자료 공간과 한 개의 포인터 공간이 있고, 각 노드의 포인터는 다음 노드를 가리킨다. <br>

#### 2. 이중 연결 리스트 <br>

![image](https://user-images.githubusercontent.com/61777583/190062543-86903a67-3eb9-4f57-b82f-f57161ad007e.png)

- 단일 연결 리스트와 비슷하지만, 포인터 공간이 두 개가 있고 각각의 포인터는 앞의 노드와 뒤의 노드를 가리킨다. <br>

#### 3. 원형 연결 리스트 <br>

![image](https://user-images.githubusercontent.com/61777583/190062560-c2928449-de77-4fea-bd07-c81fbcfc2620.png)

- 일반적인 연결 리스트에 마지막 노드와 처음 노드를 연결시켜 원형으로 만든 구조

<br>

---

<br>

### 3. 연산 🔎

#### 1. 초기화

- 가장 첫 번째 노드를 가리킬 포인터 Node* head를 전역변수로 선언하고 init() 함수를 통해 초기화한다.

```
Node* head;

void init(){
    head = NULL;
}
```

#### 2. 삽입

1. 가장 앞에 노드를 삽입하는 경우
    1. 연결 리스트가 비어 있는 경우 <br>
       ![image](https://user-images.githubusercontent.com/61777583/190073511-50a73587-1435-459a-bdf7-f5e233b87d6e.png)
       <br>
       첫번째 노드로 정수 100을 데이터로 갖는 노드를 추가한다고 가정한다. 이 경우 간단하게 newNode를 만든 후 head가 newNode를 가리키도록 하면 된다.

    - 연결 리스트가 비어 있는지 확인하는 방법 : head == null 이면 비어 있는 것이다.

    <br>

    2. 연결 리스트가 비어 있지 않은 경우 <br>
       ![image](https://user-images.githubusercontent.com/61777583/190073828-b2f5d85b-4d66-4f1a-be07-ac629b899e58.png)
       <br>
       newNode를 생성한 후 head가 가리키는 노드를 newNode의 next 포인터가 가리키게 한다. <br>
       ![image](https://user-images.githubusercontent.com/61777583/190073977-080eb1a9-3ca4-4a74-a129-14aa38179b71.png) <br>
       이후 head가 newNode를 가리키게 하면 된다.

    <br>
2. 가장 뒤에 노드를 삽입하는 경우
   ![image](https://user-images.githubusercontent.com/61777583/190074671-339379ea-c059-4c6f-8b1f-9972cf930518.png)

- 마지막 노드로 정수 300을 데이터로 갖는 노드를 추가한다고 가정한다. 이 경우 newNode를 만든 후 마지막 노드의 next 포인터가 newNode를 가리키게 하면 될 것이다.

<br>

3. 중간에 노드를 삽입하는 경우

- 연결 리스트 중간에 정수 200을 데이터로 갖는 노드를 추가한다고 가정한다. 이 경우 아래와 같은 과정을 거치면 된다.
  ![image](https://user-images.githubusercontent.com/61777583/190075529-9da598f4-1ffd-402d-8bd8-a140c8908efc.png)

1. 가장 먼저 newNode를 생성한다.
   ![image](https://user-images.githubusercontent.com/61777583/190075605-08d09106-31fc-4245-bb75-f371700a39a5.png)
2. newNode의 next 포인터가 이전 노드의 next가 가리키는 노드를 가리키도록 한다.
   ![image](https://user-images.githubusercontent.com/61777583/190075686-3a7429e7-77f8-4b9f-b6e1-487e11a63769.png)
3. 마지막으로 이전 노드의 next 포인터가 newNode를 가리키도록 하면 된다.

<br>

#### 3. 삭제

1. 가장 앞의 노드를 삭제하는 경우
    - 예를 들어, 100을 데이터로 갖는 노드를 삭제한다면, 다음과 같은 과정을 거치게 된다.
      ![image](https://user-images.githubusercontent.com/61777583/190076424-6a003772-5194-4160-b2fe-2fa8b3f80ffa.png)
      ![image](https://user-images.githubusercontent.com/61777583/190076496-8298f976-d0aa-4052-ac26-4938a4ce2a1c.png)
    - head가 cur->next를 가리키게 하고, cur->next를 NULL로 설정한다.
      ![image](https://user-images.githubusercontent.com/61777583/190076649-e2539101-835e-4aa9-8352-e61ec8e2aba4.png)
    - 이후 cur을 free 시키면 된다.

<br>

2. 가장 뒤의 노드를 삭제하는 경우 & 중간 노드를 삭제하는 경우
    - 이 경우에는 prev라는 포인터를 이용해 삭제할 노드의 이전 노드를 가리켜야 한다.
      ![image](https://user-images.githubusercontent.com/61777583/190077015-64d9ed46-4021-47f1-9ef7-c7978e32027e.png)
      초기에 prev 포인터과 cur 포인터는 모두 head가 가리키는 첫번째 노드를 가리킨다.
      ![image](https://user-images.githubusercontent.com/61777583/190077206-e339e0b9-5a83-4ebc-9ba8-1fc1ae983141.png)
      이후 cur 포인터가 다음 노드를 가리키고, 이 때 사용자가 입력한 데이터 200과 cur->data가 일치하므로 삭제 과정을 진행한다.
      ![image](https://user-images.githubusercontent.com/61777583/190077334-100621e4-2881-4b70-81b1-8714027530ea.png)
      prev->next가 cur->next를 가리키게 하고, 이후 cur->next는 NULL을 가리키게 하면 된다.
      ![image](https://user-images.githubusercontent.com/61777583/190077430-9e5b1c06-5db1-4de5-9530-f69a0a135360.png)
      이후 cur을 free 해주면 삭제가 완료된다.

<br>

#### 4. 탐색

- 사용자가 입력한 데이터가 리스트에 존재하는지 확인하는 함수는 아래와 같다.

```java
int search_list(int data){
        Node*ptr;
        for(ptr=head;ptr;ptr=ptr->next){
        if(ptr->data==data){    // data 발견  
        return 1;
        }
        }

        return-1; // 데이터 미 발견 
        }
```

---

<br>

### 4. 구현 예제 🔎

```java
#include<stdio.h>
        #include<stdlib.h>
        typedef struct _Node{
        int data;            /* 저장할 데이터 */
        struct _Node*next;    /* 다음 노드를 가리킬 포인터*/
        }Node;
        Node*head;
        void init(){
        head=NULL;
        }
        void insert(int data){
        Node*ptr;
        Node*newNode=(Node*)malloc(sizeof(Node));
        newNode->data=data;    // 데이터 할당 
        newNode->next=NULL;    // next 포인터 초기화 

        if(head==NULL){    // empty
        head=newNode;
        }else{
        // not empty, 가장 앞에 노드 추가 
        if(head->data>newNode->data){
        newNode->next=head;
        head=newNode;
        return;
        }
        // 중간에 노드 추가 
        for(ptr=head;ptr->next;ptr=ptr->next){
        if(ptr->data<newNode->data&&ptr->next->data>newNode->data){
        newNode->next=ptr->next;
        ptr->next=newNode;
        return;
        }
        }

        ptr->next=newNode;    // 마지막에 노드 추가  
        }

        }
        int deleteNode(int data){
        Node*cur,*prev;
        cur=prev=head;

        if(head==NULL){    // empty list 
        printf("error: list is empty!\n");
        return-1;
        }

        if(head->data==data){    // 가장 앞의 노드 삭
        head=cur->next;
        cur->next=NULL;
        free(cur);
        return 1;
        }

        for(;cur;cur=cur->next){    // 중간 혹은 마지막 노드 삭제
        if(cur->data==data){
        prev->next=cur->next;
        cur->next=NULL;
        free(cur);
        return 1;
        }
        prev=cur;
        }

        printf("error : there is no %d!\n",data);
        return-1;    // 해당 데이터가 리스트에 존재하지 않음 
        }
        int search_list(int data){
        Node*ptr;
        for(ptr=head;ptr;ptr=ptr->next){
        if(ptr->data==data){    // data 발견  
        return 1;
        }
        }

        return-1; // 데이터 미 발견 
        }
        void printList(){
        Node*ptr;
        for(ptr=head;ptr->next;ptr=ptr->next){
        printf("%d->",ptr->data);
        }
        printf("%d\n",ptr->data);
        }
        int main(){
        int data;

        init();
        insert(100);
        insert(300);
        insert(50);
        insert(200);
        printList();
        deleteNode(50);
        printList();
        deleteNode(200);
        printList();

        return 0;
        }
```

<br>

---

<br>

###### Reference

- https://ko.wikipedia.org/wiki/%EC%97%B0%EA%B2%B0_%EB%A6%AC%EC%8A%A4%ED%8A%B8
- https://dojang.io/mod/page/view.php?id=645
- https://code-lab1.tistory.com/2

[맨 위로 이동하기](#){: .btn .btn--primary }{: .align-right} 