---
title:  "[OS] 프로세스와 스레드의 차이점 (미완성)" 

categories:
  - OS
tags:
  - [Thread, Process, OS]

toc: true
toc_sticky: true

date: 2022-07-07
last_modified_at: 2022-07-07
---

## 프로세스와 스레드의 차이점❗️
한 프로세스가 다른 프로세스의 자원에 접근하려면 통신을 이용해야한다.
- 파이프, 파일, 소켓 등
스레드는 같은 프로세스 안에 있는 여러 스레드들은 같은 힙 공간을 공유한다. 반면에 프로세스는 다른 프로세스의 메모리에 직접 접근할 수 없다
프로세스 내에서 각각 Stack만 따로 할당받고 Code, Data, Heap 영역은 공유한다.

![Parameter](https://user-images.githubusercontent.com/61777583/177722805-fb54b110-bd0c-43fc-a46c-1eb82c60ea62.png)


