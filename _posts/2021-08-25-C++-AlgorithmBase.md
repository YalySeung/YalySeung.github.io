---

title: "AlgorithmBase"
excerpt: "알고리즘 풀이에 필요한 C++ 사용법" 

categories:
  - C++
  - Algorithm

tags:
  - [C++, Algorithm]

toc: true
toc_sticky: true
toc_label: AlgorithmBase

last_modified_at: 2021-09-10T08:00:00-10:00:00
---

## 목차
  - [입출력](#입출력)
    - [cin, cout 사용](#cin-cout-사용)
    - [scanf, printf 사용](#scanf-printf-사용)
    - [라인 단위로 입력받기](#라인-단위로-입력받기)
    - [파일 입력받기](#파일-입력받기)
  - [정렬](#정렬)
    - [sort 함수 사용](#sort-함수-사용)
    - [sort 함수 사용자 정의 정렬 ](#sort-함수-사용자-정의-정렬)
  - [Collection 원소 Iterator로 접근](#collection-원소-Iterator로-접근)
  - [Collection 에서 유용한 함수](#collection-에서-유용한-함수)
  - [다음 순열 구하기](#다음-순열-구하기)

---

### 입출력
  - #### cin, cout 사용
    * 개요
      + 헤더 : #include <iostream> 
      + cin : 공백문자 또는 개행문자 단위로 입력 받음
    * 소스 코드  

  ```c++
void main() {
	string input;
	cin >> input;

	cout << "cin 입력값 : " << input << endl;
}
  ```

    * 결과  
  ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/Algorithm/cincoutResult.png){: width="30%" height="30%"}  

  - #### scanf, printf 사용
    * 개요
      + scanf() : 입력 파일 포멧 설정 가능, 변수의 포인터로 입력을 받아야함
      + printf() : 출력 파일 포멧 설정 가능
    * 소스코드
    
  ```c++
int main() {
	int inputNum;
	char inputString[100];
	scanf("%d %s", &inputNum, &inputString);

	printf("입력받은 숫자 : %d,  입력받은 문자열 : %s", inputNum, &inputString);
}
  ```

    - 결과  
  ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/Algorithm/scanfprintfResult.png){: width="50%" height="50%"}  

  - #### 라인 단위로 입력받기
    - 개요
      - 한줄씩 입력을 받아야 할 경우 사용
      - getline() 사용
    - 소스코드
  ```c++
  int main (){
      char inputString[100];
      cin.getline(inputString, 100);
      
      cout << "입력받은 line 데이터 : " << inputString << endl;
  }
  ```

  - #### 파일 입력 받기
    - 개요
    - 소스코드
    추가예정

---

### 정렬
  - ####  sort 함수 사용
    - 개요
      - #include \<algorithm> 헤더 사용
      - pair, tuple은 첫번째원소>두번째원소>... 순으로 정렬

  - 소스코드
  ```c++
  int main()
  {
    vector<int> v;

    v.push_back(5);
    v.push_back(2);
    v.push_back(3);

    sort(v.begin(), v.end()); //오름차순
    sort(v.rbegin(), v.rend()); //내림차순
  }
  ```
  - 결과
  ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/Algorithm/CollectionSortResult.png){: width="30%" height="30%"}  

  - ####  sort 함수 사용자 정의 정렬
    - 개요 
      - #include <algorithm> 헤더 사용
      - 구조체 operator< 정의방식 / 비교함수 정의 방식 이 있음
  
  1. 구조체 연산자 오버로딩 방식
  - 소스 코드
  ```c++
  struct Sample{
      int x, y;
      bool operator<(const Sample &p) const{
          if (x == p.x) return y < p.y;
          return x < p.x;    
      }
  };
  
  int main (){
      vector<struct Sample> v;
      struct Sample s1, s2, s3;
      s1.x = 2;
      s1.y = 3;
      
      s2.x = 1;
      s2.y = 2;
      
      s3.x = 1;
      s3.y = 1;
      
      v.push_back(s1);
      v.push_back(s2);
      v.push_back(s3);
      
      sort(v.begin(), v.end());
  }
  ```

  - 결과
  
  2. 비교함수 정의 방식
  - 소스코드
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
  - 결과
  ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/Algorithm/CollectionSortResultUsingCompare.png){: width="30%" height="30%"}

---

### Collection 원소 Iterator로 접근
  - 개요
    - vector<int>::iterator it 선언
    - v.begin() : Collection의 첫 원소
    - v.end() : Colletion의 마지막 원소 다음
    - 반복자의 원소는 * 로 접근 가능
    - 출력 stream으로 변환 시 to_string 함수가 필요할 경우가 있음
  - 소스
  ```c++
  int main (){
      vector<int> v;
      v.push_back(3);
      v.push_back(1);
      v.push_back(8);
      
      for(vector<int>::iterator it = v.begin(); it != v.end(); it++){
          cout << to_string(*it) << endl;
      }   
  }
  ```

  - 결과

---

### Collection 에서 유용한 함수
  - sort() : Collection 정렬
  - reverse() : Collection 뒤집기
  - radom_shuffle() : 무작위로 섞기
  - lower_bound() : 특정 값 이상인 첫번째 원소의 Iterator 반환, 주어진 범위가 정렬되어있어야 동작, 없을경우 v.end() 반환
  - upper_bound() : 특정 값 이하인 첫번째 원소의 Iterator 반환, 주어진 범위가 정렬되어있어야 동작, 없을경우 v.end() 반환
  - v.erase() : 중복 원소 삭제

---

### 다음 순열 구하기

  - 개요
    - #include \<algorithm> 헤더 사용
    
  - 소스 코드

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
  
  - 결과
  ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/Algorithm/NextPermutationResult.png){: width="30%" height="30%"}