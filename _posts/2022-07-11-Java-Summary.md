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

last_modified_at: 2022-07-13T08:00:00-10:00:00
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
  - class 생성시 equals, tostring, hashcode(key 값 찾아올때 사용) 재정의
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

## Class 정보 획득
### Sample
  ```java
  Class cls = MyClass.class; // 정적필드
  
  Class.forName("패키지명.classname"); // 정적 메서드
  
  MyClass cls = new MyClass();
  cls.getClass(); // 객체로부터 가져오기

  ```

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

# final 키워드
## 개요
  - Read Only
  - Static final : 클래스 변수로 선언시 초기화
  - Instance final : 인스턴수 변수로 인스턴스 생성(new)시 초기화

## Sample
  - static 블럭과 인스턴스 블럭을 이용한 초기화
### 소스코드
  ```java
  public class MyClass {
        public static final int CONSTANT1 = 10;
        public static final int CONSTANT4;

        public final int CONSTANT2;
        public final int CONSTANT3;

        static{
          System.out.println("정적 초기화 블럭");
          CONSTANT4 = 40;
        }

        {
          System.out.println("인스턴스 초기화 블럭");
          CONSTANT3 = 30;
        }

        public MyClass() {
          System.out.println("생성자");
          CONSTANT2 = 20;
        }
  }
  ```
### 결과
  ![image](/assets/images/Java/FieldInitSequence.png){: width="40%" height="40%"}

---

# Exception
## 개요
  - 소스 상에서 논리적 에러가 발생하면 소스는 JVM runtime 에 에러 전달
  - JVM runtime 은 Exception 객체 생성하여 소스로 전달
  - 개발자는 이 Exception 객체를 처리해줘야 한다.
  - 클래스 선언시, throws [예외명] 명시

## 분류
  - 일반 예외 : 컴파일러 체크 예외, 컴파일 과정에서 예외처리 코드 있는지 검사
  - 실행 예외 : 컴파일러 논 체크 예외, 컴파일 과정에서 예외처리코드 검사하지 않음

## Sample
  ```java

  public static int add(int a, int b) {
    return 0;
  }

  ```

---

# Comparable<T>, Comparator<T>
## 개요
  - <T> 타입의 값 대소비교에 사용되는 인터페이스
  - CompareTo() 메소드를 구현하여 사용

## Sample
  ```java

  public class Student implements Comparable<Student> {

    private String name;
    private int age;
    private int height;

    public int compareTo(Student o) {
      return this.age - o.age;
    }
  }

  public class Main {
    public static void main(String[] args) {

      Student student1 = new Student("홍길동", 16, 170);
      Student student2 = new Student("이순신", 13, 180);
      Student student3 = new Student("강감찬", 18, 190);
      
      List<Student> studentList = new ArrayList<Student>();
      studentList.add(student1);
      studentList.add(student2);
      studentList.add(student3);
      
      studentList.sort(new Comparator<Student>() {
        public int compare(Student o1, Student o2) {
          return o1.compareTo(o2);
        }
      });

      System.out.println(studentList);
    }
  }

  ```

## 결과
  ![image](/assets/images/Java/SortResult.png){: width="100%" height="100%"}

---

# 참고서적
  - [uml for javaprogrammer] / Robert C. Martin
  - [패턴을 활용한 리팩터링] / 조슈아 케리에브스키