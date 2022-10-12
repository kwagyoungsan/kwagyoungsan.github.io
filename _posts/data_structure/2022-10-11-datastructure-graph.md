---
title:  "[Data Sturcture] 그래프(Graph)에 대해 알아보자❗️" 

categories:
  - Data Structure
tags:
  - [Graph, Data Structure]

toc: true
toc_sticky: true

date: 2022-10-11
last_modified_at: 2022-10-11
---

### 1. 정의 🔎
- Vertex(점)와 edge(변)로 구성된 한정된 자료구조
- 연결되어 있는 객체(원소) 간의 관계를 표현할 수 있는 자료 구조

<br>

---

<br>

### 2. 그래프(Graph)와 트리(Tree)의 차이 🔎
![image](https://user-images.githubusercontent.com/61777583/195375521-95973659-d786-42dd-ac8b-2eb96495fb9f.png)

### 3. 특징 🔎
- 그래프는 네트워크 모델이다.
- 2개 이상의 경로가 가능하다.
  - 즉, 노드들 사이에 무방향/방향에서 양방향 경로를 가질 수 있다.
- Self-Loop 뿐 아니라 Loop/Circuit 모두 가능하다.
- 루트 노드라는 개념이 없다.
- 부모-자식 관계라는 개념이 없다.
- 순회는 DFS나 BFS로 이루어진다.
- 그래프는 순환(Cyclic) 또는 비순환(Acyclic)이다.
- 간선의 유무는 그래프에 따라 다르다

<br>

---

<br>

### 종류

#### 1. 무방향 그래프(Undirected Graph) 🔎
- 두 정점을 연결하는 간선에 방향이 없는 그래프 <br>
![image](https://user-images.githubusercontent.com/61777583/195376721-828d227d-3d56-49c7-940c-21c87ec0a81c.png)
- 무향방 그래프에서 정점 Vi와 Vj를 연결하는 간선을 (Vi, Vj)로 표현하는데, 이때 (Vi, Vj)와 (Vj, Vi)는 같은 간선을 나타낸다.
- V(G1)={A,B,C,D}, E(G1)={(A,B), (A,D), (B,C), (B,D), (C,D)}

#### 2. 방향 그래프(Directed Graph) 🔎
- 간선에 방향이 있는 그래프 <br>
![image](https://user-images.githubusercontent.com/61777583/195377216-aef9ec98-c8d0-4859-aed2-cdb89e015a24.png) <br>
- 방향 그래프에서 정검 Vi와 Vj를 연결하는 간선을 <Vi, Vj>로 표현하는데 Vi를 꼬리(tail), Vj를 머리(head)라고 합니다. 이때







###### Reference
- https://leejinseop.tistory.com/43
- https://gmlwjd9405.github.io/2018/08/13/data-structure-graph.html
