---
title:  "[Data Sturcture] 힙(Heap)에 대해 알아보자❗️" 

categories:
  - Data Structure
tags:
  - [Heap, Data Structure]

toc: true
toc_sticky: true

date: 2022-10-13
last_modified_at: 2022-10-23
---

### 1. 정의 🔎
- 완전 이진 트리를 기초로 하는 자료구조
  - 마지막을 제외한 모든 노드에서 자식들이 꽉 채워진 이진트리

![image](https://user-images.githubusercontent.com/61777583/197396989-c865197b-41c2-4d80-9173-77a404eaaf46.png)

- 힙은 최대 힙(Max heap)과 최소 힙(Min Heap)으로 나눠진다. 최대 힙은 부모노드의 값이 자식 노드들의 값보다 항상 크고, 최소 힙은 부모 노드의 값이 자식노드의 값보다 항상 작다. 
<br>
(위 그림은 최대힙의 예시)
<br>
이러한 성질 때문에 항상 느슨한 정렬상태(반정렬 상태)를 유지합니다.

- 힙은 중복값을 허용합니다. 힙은 최댓값 또는 최솟값을 쉽게 뽑기 위한 자료구조 임으로 중복을 허용합니다.

<br>

---

<br>

### 2. 힙 재구조화 (Heapify) 🔎
- 최대힙의 부모 노드는 항상 자식 노드의 값보다 크다는 조건을 가지고 있다. 하지만 힙에서 삽입 또는 삭제가 일어나게 되면 경우에 따라 최대힙의 조건이 깨질 수 있다. 이러한 경우에 최대힙의 조건을 만족할 수 있게 노드들의 위치를 바꿔가며 힙을 재구조화(heapify) 해주어야 한다.
- 삽입과 삭제의 경우 모두 연산 자체는 O(1)로 작동하지만 heapify의 과정을 거치기 때문에 O(logn)의 시간복잡도를 가지게 된다.

#### 삽입 구현
- 새로운 노드는 리프 노드(자식 노드가 없는 노드) 가 아니면서 가장 말단에 있는 노드의 자식 노드로 추가됩니다. 이후, 부모 노드와 비교하면서 재구조화 과정을 수행한다. 삽입과정은 아래에서 위로 재구조화 과정이 이루어지게 된다.

![image](https://user-images.githubusercontent.com/61777583/197397358-54379648-76ad-4d45-bf36-b73092b93675.png)

<br>

#### 삽입 구현 코드
- 반복문을 사용하여 삽입 후 재구조화를 구현하면 다음과 같다.
```python
def up_heapify(index, heap):
    child_index = index
    while child_index != 0:
        parent_index = (child_index - 1) // 2
        if heap[parent_index] < heap[child_index]:
            heap[parent_index], heap[child_index] = heap[child_index], heap[parent_index]
            child_index = parent_index
        else:
            return

```

<br>

#### 삭제 구현
- 루트 노드가 삭제되면 가장 말단 노드를 루트 노드 자리에 대체한 후 재구조화 과정을 수행한다. 힙으로 구현된 우선순위 큐에서도 가장 우선 순위가 큰 루트 노드를 주로 삭제한다. 삽입의 경우에는 가장 말단 노드에 추가하여 재구조화 과정을 수행하면 된다. 삭제과정은 위에서 아래로 재구조화 과정이 이루어지게 된다.

![image](https://user-images.githubusercontent.com/61777583/197397580-bb7c9275-a52a-4b94-9731-02f90ef2ee28.png)

#### 삭제 구현 코드
- 반복문을 사용하여 삭제 후 재구조화를 구현하면 다음과 같다.
```python
def find_bigger_child_index(index, heap_size):
    parent = index
    left_child = (parent * 2) + 1
    right_child = (parent * 2) + 2

    if left_child < heap_size and heap[parent] < heap[left_child]:
        parent = left_child
    if right_child < heap_size and heap[parent] < heap[right_child]:
        parent = right_child
    return parent


def down_heapify(index, heap):
    parent_index = index
    bigger_child_index = find_bigger_child_index(parent_index, len(heap))
    while parent_index != bigger_child_index:
        heap[parent_index], heap[bigger_child_index] = heap[bigger_child_index], heap[parent_index]
        parent_index = bigger_child_index
        bigger_child_index = find_bigger_child_index(parent_index, len(heap))
```

- 재귀함수를 사용하면 다음과 같다.
```python
def down_heapify(array, index, heap_size):
        
        # 1. 부모노드와 자식노드들의 인덱스 지정
        parent = index
        left_child = 2 * parent + 1
        right_child = 2 * parent + 2
		
        # 2. 왼쪽 자식노드, 오른쪽 자식노드 중 가장 큰 노드를 선택
        if left_child < heap_size and array[left_child] > array[parent]:
            parent = left_child
        if right_child < heap_size and array[right_child] > array[parent]:
            parent = right_child
            
        # 3. 자식노드 중 가장 큰 노드와 부모 노드를 바꿈(배열의 값 교환)
        if parent != index:
            array[parent], array[index] = array[index], array[parent]
            
            # 4. 바뀐 자식노드의 힙을 재구조화
            make_heap(array, parent, heap_size)

```



<br>

---

<br>

###### Reference
- https://velog.io/@emplam27/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EA%B7%B8%EB%A6%BC%EC%9C%BC%EB%A1%9C-%EC%95%8C%EC%95%84%EB%B3%B4%EB%8A%94-%ED%9E%99Heap
