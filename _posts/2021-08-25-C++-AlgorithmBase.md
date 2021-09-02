---

title: "AlgorithmBase"
excerpt: "알고리즘 풀이에 필요한 C++ 사용법" 

categories:
  - C++
  - Algorithm

tags:
  - [C++, Algorithm]

last_modified_at: 2021-08-26T08:00:00-10:00:00
---


### Collection 정렬
  - ####  #include \<algorithm> sort 함수 사용

  ```c++
  int main()
  {
    vector<int> v;

    v.push_back(5);
    v.push_back(2);
    v.push_back(3);

    sort(v.begin(), v.end());
  }
  ```
  
  ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/Algorithm/CollectionSortResult.png){: width="30%" height="30%"}  

  - ####  #include \<algorithm> sort 함수 정렬 규칙 변경
    
  ```c++  
  bool compare(string before, string after) {
    return before.length() < after.length();
  }

  int main()
  {
    vector<string> names = { {"John"}, {"Tom"}, {"Jason"} };
    sort(names.begin(), names.end(), compare);
  }
  ```

  ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/Algorithm/CollectionSortResultUsingCompare.png){: width="30%" height="30%"}  

---

### 다음 순열 구하기

  - ####  #include \<algorithm> next_permutation 함수 사용

  ```c++
  int main()
  {
    string str = "abc";
    next_permutation(str.begin(), str.end());
    next_permutation(str.begin(), str.end());
    next_permutation(str.begin(), str.end());
    next_permutation(str.begin(), str.end());
    next_permutation(str.begin(), str.end());
  }
  ```
  
  ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/Algorithm/NextPermutationResult.png){: width="30%" height="30%"}  