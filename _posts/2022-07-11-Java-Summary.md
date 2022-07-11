---
title: "Java Summary"
excerpt: "자바 개요"

categories:
  - Java

tags:
  - [Java]

toc: true
toc_sticky: true
toc_label: "Java Summary"

last_modified_at: 2022-07-11T08:00:00-10:00:00
---

# JVM
## 개요
  - Java 가상 머신
  - 내부적으로 물리적 메모리와 동일하게 Stack(변수), Heap(객체), Data(static, const, class, method, enum) 영역으로 구분
  - javac.exe : 컴파일을 위한 JVM Application
  - java.exe : JVM 구동 JVM Application

---

# appication 실행

## 개요 
  - IDE 를 사용하지 않고 CMD 에서 실행
  - IDE에서 내부적으로는 이런 방식으로 동작

## Sample
  - java -cp . parent.Main 1 2 3 4 // cp -> Class Path
  - 실행 결과  
   ![image](/assets/images/Java/ApplicationExecute.png){: width="60%" height="60%"}

---

# Literal
## 개요
  - 값을 표현하는 코드상의 규약

## Sample
  ```java
    'a' // => 문자
    0.1f // => float 상수값
  ```

---

# Class
## 개요
  - class 생성시 eqauls, tostring, hashcode(역이 성립하지 않는 Value 반환 메서드 암호화시 사용) 재정의
  - Role & Responsibility 작성 : 클래스의 행위는 클래스의 데이터에 영향을 주는 행위만 정의한다.

## 객체간의 관계 
### 집합 관계
  - 부품과 완성품과의 관계
  - Field
  - Composition, Association

### 사용 관계
  - 객체 간의 상호작용
  - 메소드

### 상속 관계 
  - 키워드(implements, extends)
  - Generalization

---

# 매개변수
## 가변 매개변수
  - function(<T> ... 변수명)

## Sample
  ```java

  //메서드 정의
  public static int Sum(int ... arr){
    ...
  }

  //호출
  main(){
    MyCalc.Sum(1,2,3,4,5,6,7)
  }

  ```

---

# instance 와 static
## 개요
  - 상태가 필요없는 메서드의 경우 static 을 사용.
  - static 필드와 메서드는 this 히든 키워드 사용 불가.

## Sample
  ```java

  public static int add(int a, int b) {
    return 0;
  }

  ```

---

# 참고서적
  - [uml for javaprogrammer] / Robert C. Martin