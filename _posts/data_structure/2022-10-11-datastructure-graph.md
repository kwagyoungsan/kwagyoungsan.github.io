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
- 순회는 DFS(Depth-First Search)나 BFS(Breadth-First Search)로 이루어진다.
- 그래프는 순환(Cyclic) 또는 비순환(Acyclic)이다.
- 간선의 유무는 그래프에 따라 다르다

<br>

---

<br>

### 4. 종류

#### 1. 무방향 그래프(Undirected Graph) 🔎

- 두 정점을 연결하는 간선에 방향이 없는 그래프 <br>

![image](https://user-images.githubusercontent.com/61777583/195376721-828d227d-3d56-49c7-940c-21c87ec0a81c.png)

- 무향방 그래프에서 정점 Vi와 Vj를 연결하는 간선을 (Vi, Vj)로 표현하는데, 이때 (Vi, Vj)와 (Vj, Vi)는 같은 간선을 나타낸다.
- V(G1)={A,B,C,D}, E(G1)={(A,B), (A,D), (B,C), (B,D), (C,D)}

<br>

#### 2. 방향 그래프(Directed Graph) 🔎

- 간선에 방향이 있는 그래프 <br>

![image](https://user-images.githubusercontent.com/61777583/195377216-aef9ec98-c8d0-4859-aed2-cdb89e015a24.png) <br>

- 방향 그래프에서 정검 Vi와 Vj를 연결하는 간선을 <Vi, Vj>로 표현하는데 Vi를 꼬리(tail), Vj를 머리(head)라고 한다. 이때 <Vi, Vj>와 <Vj, Vi>는 서로 다른 간선이다.
- V(G1)={A,B,C,D} E(G1)={<A,B>, <A,D>, <B,C>, <B,D>, <C,D>}

<br>

#### 3. 완전 그래프(Complete Graph) 🔎

- 한 정점에서 다른 모든 정점과 연결되어 최대 간선 수를 갖는 그래프.

![image](https://user-images.githubusercontent.com/61777583/195378224-ff45e6f9-6f03-4ada-8e1c-9b0a82434669.png)

- 정점이 n개인 완전 그래프에서 무방향 그래프의 최대 간선 수는 n(n-1)/2이고 방향 그래프의 최대 간선 수는 n(n-1)이다.

<br>

#### 4. 부분 그래프(Subgraph) 🔎

- 기존의 그래프에서 일부 정점이나 간선을 제외하여 만든 그래프

![image](https://user-images.githubusercontent.com/61777583/195378472-4704e445-44bd-4463-8588-4ae2b65ff4b9.png)

<br>

#### 5. 가중 그래프(Weight Graph) 🔎

- 정점을 연결하는 간선에 가중치(weight)를 할당한 그래프

![image](https://user-images.githubusercontent.com/61777583/195378925-a87b5e8c-3409-4cef-8c2a-a4c5b44353a7.png)

<br>

#### 6. 유향 비순환 그래프(DAG, directed Acyclic Graph) 🔎

- 방향 그래프에서 사이클이 없는 그래프

![image](https://user-images.githubusercontent.com/61777583/195379028-49dc0917-3b72-48ec-ba0e-f69cbfb4d688.png)
<br>

#### 7. 연결 그래프(Connected Graph) 🔎

- 떨어져 있는 정점이 없는 그래프

![image](https://user-images.githubusercontent.com/61777583/195379284-37f3971d-3381-436c-a290-d99f16f24b1c.png)

<br>

#### 8. 단절 그래프(Disconnected Graph) 🔎

- 연결되지 않은 정점이 있는 그래프

![image](https://user-images.githubusercontent.com/61777583/195379284-37f3971d-3381-436c-a290-d99f16f24b1c.png)

<br>

---

<br>

### 5. 그래프 용어 🔎

- 그래프에서 두 정점 Vi와 Vj가 연결되어 간선 (Vi, Vj)가 있을 때, 두 정점 Vi와 Vj를 인접(adjacent)한다 하고, 간선 (Vi, Vj)는 정점 Vi와 Vj에 부속(incident)되어 있다고
  말한다.
- 차수(Dgree): 정점에 부속되어 있는 간선의 수
    - 진입차수(in-degree): 정점을 머리로 하는 간선의 수
    - 진출차수(out-degree): 정점을 꼬리로 하는 간선의 수
- 경로(Path): 정점 Vi에서 Vj까지 간선으로 연결된 정점을 순서대로 나열한 리스트
    - 단순 경로(Simple Path): 모두 다른 정점으로 구성된 경로
    - 경로 길이(Path Length): 경로를 구성하는 간선의 수
- 사이클(Cycle): 단순 경로 중에서 경로의 시작 정점과 마지막 정점이 같은 경로

<br>

---

<br>

### 6. 그래프 탐색 🔎

- BFS
    - 정점을 기준으로 간선이 연결되어 있는 모든 정점들을 차례로 방문하고 찾고자 하는 정점을 만날 때까지 반복한다.
    - 일반적으로 Queue를 사용해서 구현한다.
- DFS
    - 정점을 기준으로 간선이 연결되어 있는 정점들 중 하나를 선택해 이동하고 다시 이동한 정점을 기준으로 다시 인접 정점을 선택한다 연결되어 있는 간선을 따라 찾고자 하는 정점을 만날 때까지 진행하고 찾지
      못하면 다시 이전 정점으로 돌아와 반복한다.
    - 재귀함수 또는 Stack을 사용해서 구현한다.

<br>

--- 

<br>

### 7. 그래프 구현 방법 🔎

1. 인접 행렬

- 2차원 배열로 그래프를 구현하는 방식

![image](https://user-images.githubusercontent.com/61777583/195381370-ca2192c9-a470-41d4-b0be-559a599629d5.png)

- 간선이 존재하는 두 정점 칸은 1로 없는 칸은 0으로 채워주고 만약 가중치가 다른 그래프라면 해당 가중치 값을 넣어준다.
- 2차원 배열상에 그래프 정보가 모두 담겨 있기 때문에 간선의 존재 여부나 가중치를 알고 싶을 땐 바로 참조할 수 있다 : O(1)
  간단하게 구현할 수 있다.
- 하지만 N^N 크기의 2차원 배열을 사용하기 때문에 메모리가 필요 이상으로 많이 사용될 수 있다. (10000개의 정점으로 구성된 그래프 내에 간선이 5개만 존재할 경우)
  모든 간선 정보를 대입하는데에 시간이 걸린다 : O(N^N)


2. 인접 그래프

- 정점에 연결되어 있는 정점들만 리스트로 나타내는 그래프 표현 방식

![image](https://user-images.githubusercontent.com/61777583/195381448-96f7e5f3-9c9d-40f3-9662-6533b67b5ac4.png)

- 필요한 만큼의 메모리만 사용하기 때문에 메모리 낭비가 없고
  정점들의 연결 정보를 확인하려 할 때는 간선의 갯수만큼의 탐색이 필요하다.
    - O(N) (N = 정점에 연결된 간선 수)
      이 과정이 인접 행렬에 비해서는 오래 걸릴 수 있다. (모든 노드가 10000개 인데 1번 노드에 9999개의 간선이 존재하는 경우 9999번째 인접 정점을 확인하는데는 9999번의 탐색이 필요)

<br>

---

<br>

###### Reference

- https://leejinseop.tistory.com/43
- https://gmlwjd9405.github.io/2018/08/13/data-structure-graph.html
- https://velog.io/@nnnyeong/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EA%B7%B8%EB%9E%98%ED%94%84-Graph
