---
title:  "[Design Pattern] 안드로이드 디자인 패턴을 알아보자 ! (MVC, MVP, MVVM)" 

categories:
  - Android Design Pattern
tags:
  - [MVVM ,MVP , MVC, Android Design Pattern]

toc: true
toc_sticky: true

date: 2022-07-06
last_modified_at: 2022-07-06
---

## MVC

![Controller](https://user-images.githubusercontent.com/61777583/177506978-a53cca03-4d38-45e3-94bd-c7559d75071f.png)


### 1. 구조
- Model : 어플리케이션에서 사용되는 데이터와 그 데이터를 처리하는 부분
- View : 사용자에서 보여지는 UI 부분
- Controller : 사용자의 입력을 받고 처리하는 부분


### 2. 동작 순서
    1. 사용자의 Action들은 Controller에 들어오게 된다.
    2. controller는 사용자의 Action을 확인하고, Model을 업데이트한다.
    3. Controller는 Model을 나타내줄 View를 선택한다.
    4. View는 Model을 이용하여 화면을 나타낸다.

### 3. 특징
- Controller는 여러 개의 View를 선택할 수 있는 1:n 구조이다.
- Controller는 View를 선택할 뿐 직접 업테이트 하지 않는다.

### 4. 장점
- 널리 사용되고 있는 패턴이라는 점에서 구조가 단순하다.
- 보편적으로 많이 사용된다.

### 5. 단점
- View와 Model 사이의 의존성이 높다.
- View와 Model의 높은 의존성은 어플리케이션이 커질수록 복잡해지고 유지보수가 어렵게 된다.

<br>

***


## MVP

![Presenter](https://user-images.githubusercontent.com/61777583/177508534-d6706cca-3f5f-4e9e-a7a7-0dbd1b5d2447.png)

### 1. 구조
- Model : 어플리케이션에서 사용되는 데이터와 그 데이터를 처리하는 부분
- View : 사용자에서 보여지는 UI 부분
- Presenter : View에서 요청한 정보로 Model을 가공하여 View에 전달해주는 부분

### 2. 동작 순서
    1. 사용자의 Action들은 View를 통해 들어오게 된다.
    2. View는 데이터를 Presenter에 요청한다.
    3. Presenter는 Model에게 데이터를 요청한다.
    4. Model은 Presenter에서 요청받은 데이터를 응답한다.
    5. Presenter는 View에게 데이터를 응답한다.
    6. View는 presenter가 응답한 데이터를 이용하여 화면을 나타낸다.

### 3. 특징
- Presenter는  View와 Model의 인스턴스를 가지고 있어 둘을 연결하는 역할을 한다.
- Presenter와 View는 1:1 관계이다.

### 4. 장점
- View와 Model의 의존성이 없다.

### 5. 단점
- View와 Presenter 사이의 의존성이 높다.
- 어플리케이션이 복잡해질수록 View와 Presenter의 의존성이 높아진다.

<br>

***

## MVVM

![View Model](https://user-images.githubusercontent.com/61777583/177508750-cd2697ce-2ed5-4298-8608-a63272f9d503.png)

### 1. 구조
- Model : 어플리케이션에서 사용되는 데이터와 그 부분을 처리하는 부분
- View : 사용자에서 보여지는 UI 부분
- View Model : View를 표현하기 위해 만든 View를 위한 Model. View를 나타내 주기 위한 Model이자 View를 나타내기 위한 데이터 처리를 하는 부분

### 2. 동작 순서
    1. 사용자의 Action들은 View를 통해 들어오게 된다.
    2. View에 Action이 들어오면, Command 패턴으로 View Model에 Action을 전달한다.
    3. View Model을 Model에게 데이터를 요청한다.
    4. Model은 View Model에게 요청받은 데이터를 응답한다.
    5. View Model은 응답 받은 데이터를 가공하여 저장한다.
    6. View는 View Model과 Data Binding하여 화면을 가공한다.

### 3. 특징
- Command 패턴과 Data Binding을 이용하여  View와 View Model 사이의 의존성을 없앴다.

### 4. 장점
- View와 Model 사이의 의존성이 없다.
- View와 View Model 사이의 의존성이 없다.
- 각각의 부분은 독립적이기 때문에 모듈화하여 개발할 수 있다.

### 5. 단점
- View Model의 설계가 쉽지 않다.

<br>
<br>

###### Reference
<br>




[맨 위로 이동하기](#){: .btn .btn--primary }{: .align-right} 