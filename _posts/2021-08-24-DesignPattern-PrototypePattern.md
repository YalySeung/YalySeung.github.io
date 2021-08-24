---

title: "Prototype Pattern"
excerpt: "객체 복사를 이용해 자원 아끼기" 

categories:
  - Design Pattern

tags:
  - [Design Pattern]

last_modified_at: 2021-08-24T08:00:00-10:00:00
---


### 개요
 - 새로운 객체 생성시, 기존에 생성된 객체가 있으면 복사하여 사용하는 디자인 패턴
 - 객체 생성에 필요한 리소스를 줄일 수 있음

---

### 구성도
　　![image](/assets/images/DesignPattern/PrototypePattern.png){: width="70%" height="70%"}  

 - #### Explain
   - <span style="color:red">InstanceMaker Class</span> : Client Class
     - GetInstance() : Prototype 형식의 Instance를 생성하는 메서드  

   - <span style="color:red">Prototype Class</span> : 객체 복사 기능을 가진 Interface or Abstract Class
     - Clone() : 객체 복사
  
   - <span style="color:red">PrototypeImpl1, PrototypeImpl2 Class</span> : Prototype을 구현한 Class
     - Clone() : 객체 복사
   
---
### 구현방법
 - <span style="color:blue">Prototype Class</span> 정의
 - <span style="color:blue">Prototype Class</span> 을 구현한 <span style="color:yellow">PrototypeImpl1, PrototypeImpl2 Class</span>를 정의
 - <span style="color:red">InstanceMaker Class</span>에서 객체가 필요할 경우 GetInstance() 메서드를 통해 복제된 Prototype 객체 획득
