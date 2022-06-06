---
title: "Python Syntax"
excerpt: "파이썬 문법"

categories:
  - Python

tags:
  - [Python]

toc: true
toc_sticky: true
toc_label: "Python Syntax"

last_modified_at: 2022-06-05T08:00:00-10:00:00
---

# 출력

## 개요
  - 콘솔에 데이터를 출력
  - print(데이터) 사용  
  - <span style="color:red">복합데이터는 출력시, 데이터 사이에 공백이 추가됨</span>

## Sample
  ```python
    print("hello world") --> 문자열 출력
    print(1, "hello world") --> 복합 데이터형식 출력
  ```
---

# 입력

## 개요
  - input() 사용
  - 무엇을 입력하든 문자열로 인식됨

## Sample
  ```python
    inputValue = input()
  ```
---

# 주석

## 개요
  - 소스 관련 comment 입력
  - ''' 또는 """ 사용

## Sample
  ```python
    '''
    작은따옴표 주석이요
    '''

    """
    큰따옴표 주석이요
    """
  ```
---

# 시퀀스(sequence)

## 개요
  - 문자열, [리스트](#리스트list), [튜플](#튜플tuple) 포함하는 자료형
  - 인덱싱, 슬라이싱, in키워드, len() 함수 사용가능
  - \+ 연산자를 통한 데이터 연결, * 연산자를 통한 데이터 반복 가능

---

# 리스트(list)

## 개요
  - 일련의 데이터 저장
  - [] 사용
  - 다른형식의 데이터 저장 가능
  - list.append([값]) -> 마지막 원소 뒤에 한개의 원소 추가
  - list.insert([위치], [값])
  - list.remove([값]) --> 값과 일치하는 첫번째 원소 제거
  - list.sort() --> 숫자형은 오름차순, 문자열은 사전순 정렬 (같은 자료형만 정렬가능)
  - list.pop([인덱스]) --> 인덱스에 해당하는 원소를 제거하고 반환, 인덱스가 없을경우 마지막 원소를 제거하고 반환
  - list.count([값]) --> 값과 일치하는 원소의 개수를 반환

## Sample
  ```python
    nameList = ["Tom", "Jenny", "John", "Mike"]
    nameList.append("Shane") --> ["Tom", "Jenny", "John", "Mike", "Shane"]
    nameList.insert(1, "Jenny") --> ["Tom", "Jenny", "Jenny", "John", "Mike", "Shane"]
    nameList.remove("Jenny") --> ["Tom", "Jenny", "John", "Mike", "Shane"]
    nameList.sort() --> ["Jenny", "John", "Mike", "Shane", "Tom"]
    nameList.pop(1) --> ["Jenny", "Mike", "Shane", "Tom"]
    nameList("Tom") --> 1
  ```
---

# 튜플(tuple)

## 개요
  - 값을 바꿀수 없으면서, 여러 자료를 담을 수 있는 자료형
  - 인덱싱과 슬라이싱 가능
  - () 사용
  - <span style="color:red">데이터 추가, 삭제, 변경 불가</span>

## Sample
  ```python
    //선언
    tuple_zero = ()
    tuple_one = (1,)
    tuple_ = (1, 2, 3, 4, 5)
    tuple_ = 1, 2, 3, 4, 5
  ```
---

# 딕셔너리(dictionary)

## 개요
  - {} 사용
  - 각 원소는 key,value 데이터쌍을 이루고 있음
  - key값으로 value값을 알 수 있음
  - dic[[key값]] : key값에 해당하는 value값을 반환
  - dic[[key값]] = value값 : 원소 추가
  - del dic[[key값]] : key 값에 해당하는 원소를 지운다
  - key값은 변경 불가능 --> 리스트는 key값으로 사용 불가능, 튜플은 key값으로 사용 가능
  - dic.keys() : 모든 key값 반환
  - dic.values() : 모든 value값 반환

## Sample
  ```python
    dic_zero = {}
    person = {'name':'john', 'age':20}
    person['name'] --> 'john'
    person['address'] = '서울' // 원소 추가
    del person['name'] // 원소 제거
    person = {(1, 2, 3):'안녕'}
    person.keys() --> ('name', 'age')
    person.values() --> (john', 20)
  ```
---

# 인덱싱(tuple)

## 개요
  - sequence[index] 를 사용하여 원소값 반환

## Sample
  ```python
    persons = ['Mike', "John", "Tom"]
    persons[1] --> "John"
  ```
---

# 슬라이싱

## 개요
  - 시퀀스를 분리하거나 특정값을 추출
  - 리스트 슬라이싱 --> 리스트
  - 문자열 슬라이싱 --> 문자열
  - sequence[[시작인덱스]:[종료인덱스]] --> <span style="color:red">종료 인덱스의 원소는 포함되지 않음</span>
  - sequence[-1] --> 뒤에서 첫번째 원소 값
  - sequence[:3] --> 처음부터 index 2 원소까지 슬라이싱
  - sequence[2:] --> index 2 원소부터 끝 원소까지 슬라이싱
  - [값] in sequence --> 값이 리스트 안에 있는지 확인
  - len(sequence) --> 리스트의 원소갯수 반환
  - sequence1 + sequence2 --> 리스트 Add
  - sequence * 3 --> 해당 리스트 반복
  - sequence.split([문자열]) --> 문자열을 기준으로 시퀀스를 분할, 문자열이 없을 경우 공백을 기준으로 분할
  - str.join(sequence) --> 시퀀스 각 원소에 str 구분자를 추가하여 merge한 후 반환

## Sample
  ```python
    stringValue = "ap,ple"
    arr1 = ['A', 'B', 'C', 'D']
    arr2 = ['a', 'b', 'c']

    arr1[1, 2] --> ['B']
    arr1[1:] --> ['B', 'C', 'D']
    arr1[:3] --> ['A', 'B', 'C']
    'B' in arr --> True
    len(arr1) --> 4
    arr1 + arr2 --> ['A', 'B', 'C', 'D', 'a', 'b', 'c']
    arr2 * 2 --> ['a', 'b', 'c', 'a', 'b', 'c']
    stringValue.split(,) --> ['ap', 'ple']
    '&'.join(arr1) --> 'a&b&c'
  ```
---

# 특수연산자

## 개요

### 숫자
  - // : 나눈 몫
  - ** : 거듭제곱

### 문자열
  - \* : 해당 문자 횟수만큼 반복입력

## Sample
  ```python
    1 // 10 --> 0
    2 ** 10 --> 1024
  ```
---

# 반복문

## 개요

### while
  - 조건식이 참인동안 수행할 로직을 반복
  - while [조건식] :
      수행할 로직

### for
  - 시퀀스에서 원소를 하나씩 가져와서 사용
  - len(list) 의 크기만큼 반복
  - for [변수] in [문자열, 리스트, 튜플]:
      수행할 로직

### for range
  - range(a, b) : a값부터 1씩 증가하며 <span style="color:red">b-1까지</span> 포함하는 시퀀스를 반환 
  - range(a) : range(0, a) 와 동일, 0부터 a-1를 포함하는 시퀀스 생성
  ```python
    for i in range(4):
      수행할 로직

    //수행할 로직을 4번 반복!
  ```

### break
  - 반복문을 탈출하는 키워드

## Sample
  ```python
    starCount = 1
    while starCount <= 5:
      print("*"*starCount)
      starCount += 1

    arr = [1, 2 ,3 ,4, 5]
    for i in arr:
      print(i)
  ```
---

# 형변환

## 개요
  - 데이터간 타입 변환
  - 바꿀자료형(데이터) 사용
  - int, float, str, list
  - type(데이터) : 데이터의 자료형 반환

## Sample
  ```python
    value = "1"
    intValue = int(value)
    floatValue = float(value)
  ```
---

# Bool 연산자

## 개요
  - and : 그리고 연산
  - or : 또는 연산
  - not : 부정 연산

## Sample
  ```python
    isFalse = 1 == 2 and True
    isTrue = False or 2 == 2
    notValue = not True
  ```
---

# 조건문

## 개요
  - if 조건 :
      수행할 명령
    elif 조건:
      수행할 명령
    else :
      수행할 명령
  - <span style="color:red">같은 들여쓰기로 수행명령 구분하므로, 들여쓰기에 주의!</span>

## Sample
  ```python
    if input > 1:
      print("if 조건문 실행!")
    elif input < 0:
      print("elif 조건문 실행!")
    else:
      print("else문 실행!")
  ```
---

# 함수, 메서드

## 함수

### 개요
  - 특정 기능을 하는 코드뭉치
  - 내장 함수 : 파이썬에 내장된 함수들  
    ex) print(), input(), max(), min(), sum(), len()

## 메서드

### 개요
  - 특정 자료에 대해 특정 기능을 하는 코드
  - ex) list.append()
  

## Sample
  ```python
    max(1, 2, 3, 4, 5) // 시퀀스 자료에서 최대 값을 반환
    min([1, 2, 3, 4, 5]) // 시퀀스 자료에서 최대 값을 반환
    sum((1,2, 3, 4, 5)) // 시퀀스 자료의 합 반환
    len("name") // 시퀀스 자료의 길이 반환

    //사용자 지정 함수 정의
    def addValue(a, b):
      return a + b
  ```
---