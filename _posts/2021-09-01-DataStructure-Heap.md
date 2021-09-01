---

title: "Heap"
excerpt: "O(Logn)의 복잡도로 최대값, 최솟값 구하기" 

categories:
  - DataStructure

tags:
  - [DataStructure]

last_modified_at: 2021-09-01T08:06:00-05:00

---

### 목차
  - [개요](#개요)
  - [종류](#종류)
  - [삽입과 삭제 로직](#삽입과 삭제 로직)

---

### 개요
  - 완전이진트리의 한 종류
  - 최대값이나 최솟값을 빠르게 찾기 위한 DataStructure
  - 중복값 허용
  
---

### 종류
  - MinHeap(최소 힙) : 부모 노드의 키값이 자식 노드의 키값보다 작거나 같은 완전이진트리
  ![image](/assets/images/DataStructure/MinHeap.png){: width="40%" height="40%"}  

  - MaxHeap(최대 힙) : 부모 노드의 키값이 자식 노드의 키값보다 크거나 같은 완전이진트리
  ![image](/assets/images/DataStructure/MaxHeap.png){: width="40%" height="40%"}  

---

### 삽입과 삭제 로직
  - MinHeap
    - 삽입
      1. 새로운 요소가 Add되면 마지막 노드에 삽입
      2. <span style="color:red">부모 노드 > 새로운 노드</span> 이면 Swap
      3. 1~2번 과정 반복  
      ![image](/assets/images/DataStructure/MinHeapAdd.png){: width="40%" height="40%"}  
        
    - 삭제
      1. root 노드 제거
      2. 마지막 노드를 root 노드로 이동
      3. root 노드와 왼쪽 자식 노드, 오른쪽 자식노드중 큰 키값을 가진 자식노드돠 비교하여, <span style="color:red">root 노드의 키값이 클 경우</span> swap
      4. 1~3번 과정을 반복  
      ![image](/assets/images/DataStructure/MinHeapRemove.png){: width="40%" height="40%"}  
  
  - MaxHeap
    - 삽입
      1. 새로운 요소가 Add되면 마지막 노드에 삽입
      2. <span style="color:blue">부모 노드 < 새로운 노드</span> 이면 Swap
      3. 1~2번 과정 반복  
      ![image](/assets/images/DataStructure/MaxHeapAdd.png){: width="40%" height="40%"}  


    - 삭제
      1. root 노드 제거
      2. 마지막 노드를 root 노드로 이동
      3. root 노드와 왼쪽 자식 노드, 오른쪽 자식노드중 작은 키값을 가진 자식노드돠 비교하여, <span style="color:blue">root 노드의 키값이 작을  경우</span> swap
      4. 1~3번 과정을 반복  
      ![image](/assets/images/DataStructure/MaxHeapRemove.png){: width="40%" height="40%"}  