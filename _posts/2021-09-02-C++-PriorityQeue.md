---

title: "Priority Queue"
excerpt: "Queue에 우선순위를 부여" 

categories:
  - C++
  - DataStructure

tags:
  - [C++, DataStructure]

last_modified_at: 2021-09-02T08:00:00-10:00:00
---

---

### 목차
  - [개요](#개요)
  - [기본 정렬](#기본-정렬)
  - [오름차순 정렬](#오름차순-정렬)
  - [내림차순 정렬](#내림차순-정렬)
  - [사용자 정의 정렬](#사용자-정의-정렬)

---

### 개요
  - Heap 기반의 Queue
  - Queue Items에 우선순위가 필요할 경우 사용
  - #include \<queue>

---

### 기본 정렬
  - 소스코드

  ```c++
  vector<int> input = {-5, 8, -7, 2, 3, 1};

  void InitDefaultPriorityQueue(vector<int> input) {
	priority_queue<int> pq;
	for (int i = 0; i < input.size(); i++) pq.push(input.at(i));
  }
  ```

  - 정렬 결과
  
  ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/DataStructure/DefaultPriorityQueueResult.png){: width="30%" height="30%"}  

---

### 오름차순 정렬
  - 소스코드

  ```c++
  vector<int> input = {-5, 8, -7, 2, 3, 1};

  void InitMinPriorityQueue(vector<int> input) {
	priority_queue<int, vector<int>, greater<int>> pq;
	for (int i = 0; i < input.size(); i++) pq.push(input.at(i));
  }
  ```

  - 정렬 결과
  
  ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/DataStructure/MaxPriorityQueueResult.png){: width="30%" height="30%"}  

---

### 내림차순 정렬
  - 소스코드

  ```c++
  vector<int> input = {-5, 8, -7, 2, 3, 1};

  void InitMaxPriorityQueue(vector<int> input) {
	priority_queue<int, vector<int>, less<int>> pq;
	for (int i = 0; i < input.size(); i++) pq.push(input[i]);
  }
  ```

  - 정렬 결과
  
  ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/DataStructure/MinPriorityQueueResult.png){: width="30%" height="30%"}  

---

### 사용자 정의 정렬
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
  
  ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/DataStructure/CustomPriorityQueueResult.png){: width="30%" height="30%"}  

