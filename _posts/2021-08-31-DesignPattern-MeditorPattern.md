---

title: "Mediator Pattern"
excerpt: "클래스간 상호작용을 하나의 클래스로 위임" 

categories:
  - Design Pattern

tags:
  - [Design Pattern]

last_modified_at: 2021-08-31T08:00:00-10:00:00
---

### 목차
 - [개요](#개요)
 - [구성도](#구성도)
 - [구현방법](#구현방법)

---

### 개요
 - 객체간 상호작용을 캡슐화하여 하나의 클래스에 위임하는 디자인 패턴
 - Mediator(중재자) 가 상황에 따라 각 Colleague(상호작용 객체) 의 상태를 확인하고, 행위를 지시

---

### 구성도
　　![image](/assets/images/DesignPattern/MediatorPattern.png){: width="70%" height="70%"}  

 - #### Explain
   - <span style="color:red">Mediator Interface</span> : 중재자 Class
     - Mediate() : 상황에 따라 Colleague에게 명령을 하는 Method

   - <span style="color:red">ConcreteMediator Class</span> : Mediator 구현 Class
     - Mediate() : 상황에 따라 Colleague에게 명령을 하는 Method

   - <span style="color:red">Colleague Class</span> : 상호작용하는 Class
     - GetState() : 자신의 상태를 반환하는 Method
     - Action() : 행위 Method

   - <span style="color:red">ConcreteColleagueA, ConcreteColleagueB Class</span> : Colleague 구현 객체
     - Action() : 행위 Method
   
---
### 구현방법
 - 상호작용하는 객체의 상태와 행위를 정의하는 <span style="color:blue">Colleague</span> Interface를 선언
 - <span style="color:yellow">ConcreteColleagueA, ConcreteColleagueB</span>에 자신의 상태와 행위를 정의
 - <span style="Color:red">Concrete Mediator</span>는 ConcreteColleague List를 인스턴스 변수로 소유
 - <span style="Color:red">Concrete Mediator</span>에서 ConcreteColleague들의 상태에 따라 명령을 수행하는 Mediate Method 구현
