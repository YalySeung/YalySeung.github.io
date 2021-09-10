---

title: "Visitor Pattern"
excerpt: "복합체를 방문하여 정보를 얻자" 

categories:
  - Design Pattern

tags:
  - [Design Pattern]

last_modified_at: 2021-08-28T08:00:00-10:00:00
---

### 목차
 - [개요](#개요)
 - [구성도](#구성도)
 - [구현방법](#구현방법)

---

### 개요
 - 방문자와 방문 공간을 분리
 - Client를 대신하여 방문 공간에 대한 정보를 획득
 - Composit Pattern과 같이 사용

---

### 구성도
　　![image](/assets/images/DesignPattern/VisitorPattern.png){: width="70%" height="70%"}  

 - #### Explain
   - <span style="color:red">Client Class</span> : Visitor에게 방문을 요청하는 사용자 Class

   - <span style="color:red">Visitor Class</span> : Visitor Interface
     - Visit() : Element를 인자로 전달받아, 방문하는 Method

   - <span style="color:red">ConcreteVisitor Class</span> : Visitor 구현 Class
     - Visit() : Element를 인자로 전달받아, 방문하는 Method  

   - <span style="color:red">Element Class</span> : Element Interface
     - Accept() : 정보 전달 Method

   - <span style="color:red">ConcreteElement Class</span> : Element 구현 Class
     - Accept() : 정보 전달 Method
   
---
### 구현방법
 - <span style="color:blue">Visitor</span>에 방문공간에 대한 정보를 얻는 로직 구현
 - <span style="color:blue">Element</span>의 Accept() Method에 visitor.Visit(this) 를 통해 <span style="color:blue">Visitor</span>에게 정보 알림
