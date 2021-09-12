---

title: "Priority Queue"
excerpt: "Queue에 우선순위를 부여" 

categories:
  - C++
  - DataStructure

tags:
  - [C++, DataStructure]

toc: true
toc_sticky: true
toc_label: "Priority Queue"

last_modified_at: 2021-09-12T08:00:00-10:00:00
---

# 개요
  - Heap 기반의 Queue
  - Queue Items에 우선순위가 필요할 경우 사용
  - #include \<queue>
  - 추가, 삭제 시간복잡도 O(log n)

---

# 함수
  - push() : 원소 삽입
  - pop() : 원소 제거
  - front() : 마지막 원소 get

---

# 기본 정렬
  - 소스코드

    ```c++
      vector<int> input = {-5, 8, -7, 2, 3, 1};

      void InitDefaultPriorityQueue(vector<int> input) {
      priority_queue<int> pq;
      for (int i = 0; i < input.size(); i++) pq.push(input.at(i));
      }
    ```

  - 정렬 결과

    ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/C++/DefaultPriorityQueueResult.png){: width="30%" height="30%"}  

---

# 오름차순 정렬
  - 소스코드

    ```c++
      vector<int> input = {-5, 8, -7, 2, 3, 1};

      void InitMinPriorityQueue(vector<int> input) {
        priority_queue<int, vector<int>, greater<int>> pq;
        for (int i = 0; i < input.size(); i++) pq.push(input.at(i));
      }
    ```

  - 정렬 결과

    ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/C++/MaxPriorityQueueResult.png){: width="30%" height="30%"}  

---

# 내림차순 정렬
  - 소스코드

    ```c++
      vector<int> input = {-5, 8, -7, 2, 3, 1};

      void InitMaxPriorityQueue(vector<int> input) {
        priority_queue<int, vector<int>, less<int>> pq;
        for (int i = 0; i < input.size(); i++) pq.push(input[i]);
      }
    ```

  - 정렬 결과

    ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/C++/MinPriorityQueueResult.png){: width="30%" height="30%"}  

---

# 사용자 정의 정렬
  - 소스코드

    ```c++
      vector<int> input = {-5, 8, -7, 2, 3, 1};
      
      //절대값이 큰 순서대로 정렬
      struct compare {
        bool operator() (int pre, int post) {
          return pre * pre < post* post;
        }
      };

      void InitCustomPriorityQueue(vector<int> input) {
        priority_queue<int, vector<int>, compare> pq;
        for (int i = 0; i < input.size(); i++) pq.push(input[i]);
      }
    ```

  - 정렬 결과

    ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/C++/CustomPriorityQueueResult.png){: width="30%" height="30%"}  

