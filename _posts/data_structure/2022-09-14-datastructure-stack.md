---
title:  "[Data Sturcture] 스택(Stack)에 대해 알아보자❗️"

categories:

- Data Structure
  tags:
- [Stack, Data Structure]

toc: true
toc_sticky: true

date: 2022-09-14
last_modified_at: 2022-09-14
---

## 스택(Stack)이란? 🔎

### 1. 정의 🔎

- 한 쪽 끝에서만 자료를 넣거나 뺄 수 있는 LIFO(Last In First Out) 형식의 선형 구조
  ![image](https://user-images.githubusercontent.com/61777583/190069028-cb0f64e1-6c5a-4404-844e-c20d529bf7de.png)

<br>

---

<br>

### 2. 연산 🔎

- pop()
    - 스택에서 가장 위에 있는 항목을 제거한다.
- push(item)
    - item 하나를 스택의 가장 윗 부분에 추가한다.
- peek()
    - 스택의 가장 위에 있는 항목을 반환한다.
- isEmpty()
    - 스택이 비어있을 때, true를 반환한다.

<br>

---

<br>

### 3. 구현 예제 🔎

```C
/* Stack Example */

#include <stdio.h>
#include <stdlib.h>
#include <conio.h>

int Stack[10];
int top=-1;

int push(int dat);
int pop(void);
int printstack(void);

int main(void) {
	int inval, innum;
	printf(" - Algorithm Stack - \n");
	printf("Made by POM(lovebeen04@gmail.com)\n");
	printf("=================================\n");
	printf("1. Push Value\n");
	printf("2. Pop Value\n");
	printf("3. Print Stack\n");
	printf("4. Exit\n");
	printf("=================================\n");
	printf("> Enter Number: ");
	scanf("%d", &inval);

	switch(inval) {
		case 1:
			system("cls");
			printf("> Enter Number: ");
			scanf("%d", &innum);
			push(innum);
			break;
		case 2:
			pop();
			break;
		case 3:
			printstack();
			break;
		case 4:
			system("pause");
			break;
		default:
			system("cls");
			printf(" Error\n");
			break;
	}

	return 0;
}

int push(int dat) {
	if(top >= 9) {
		system("cls");
		printf("Stack Overflow\n");
		getch();
		system("cls");
		main();
	} else {
		top++;
		Stack[top] = dat;
		system("cls");
		printf("Push %d\n", dat);
		getch();
		system("cls");
		main();
	}
}

int pop(void) {
	system("cls");
	if(top <= -1) {
		system("cls");
		printf("Stack Downflow\n");
		getch();
		system("cls");
		main();
	} else {
		Stack[top] = 0;
		top--;
		main();
	}
}
int printstack(void) {
	int a;
	system("cls");
	printf("=================================\n");
	for(a=9; a>=0; a--) printf("%d\n", Stack[a]);
	printf("=================================\n");
	getch();
	system("cls");
	main();
}
```

<br>

---

<br>

### 4. 사용 사례 🔎

- 재귀 알고리즘
    - 재귀적으로 함수를 호출해야 하는 경우에 임시 데이터를 스택에 넣어준다.
    - 재귀함수를 빠져 나와 퇴각 검색(backtrack)을 할 때는 스택에 넣어 두었던 임시 데이터를 빼줘야 한다.
    - 스택은 이런 일련의 행위를 직관적으로 가능하게 해준다.
    - 또한, 스택은 재귀 알고리즘을 반복적 형태(iterative)를 통해서 구현할 수 있게 해준다.
- 웹 브라우저 방문기록(뒤로가기)
- 실행 취소(undo)
- 역순 문자열 만들기
- 수식의 괄호 검사(연산자 우선순위 표현을 위한 괄호 검사)
- 후위 표기법 계산

<br>

---

<br>

###### Reference

- https://ko.wikipedia.org/wiki/%EC%8A%A4%ED%83%9D
- https://gmlwjd9405.github.io/2018/08/03/data-structure-stack.html

[맨 위로 이동하기](#){: .btn .btn--primary }{: .align-right} 