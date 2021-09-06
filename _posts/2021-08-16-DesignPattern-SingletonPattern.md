---

title: "Singleton Pattern"
excerpt: "프로세스 내에서 한개만 존재하는 객체" 

categories:
  - Design Pattern

tags:
  - [Design Pattern]

last_modified_at: 2021-08-16T08:06:00-05:00
---

### 목차
 - [개요](#개요)
 - [구성도](#구성도)
 - [구현방법](#구현방법)

---

### 개요
 - 해당 클래스 인스턴스가 하나
 - 하나의 인스턴스에 대한 전역접근 제공
 - 객체 생성 부분에서 쓰레드 동기화 처리(syncronized, lock...) 필요

---

### 구성도
　　![image](/assets/images/DesignPattern/SingletonPattern.png){: width="70%" height="70%"}  

 - #### Explain
   - <span style="color:red">Singleton</span> : Singleton Class
     - intance : 하나만 존재하는 객체 instance
     - static Singleton GetInstance() : Singleton 객체에 대한 전역 접근 Method

---
### 구현방법
 - Singleton Class에 <span style="color:red">private static 인스턴스</span>를 정의
 - <span style="color:red">private static 인스턴스</span>의 Getter 정의
 - Getter에서 <span style="color:red">private static 인스턴스</span> 가 존재하지 않을 경우 new
 - 객체 new 부분에 쓰레드 동기화 처리
