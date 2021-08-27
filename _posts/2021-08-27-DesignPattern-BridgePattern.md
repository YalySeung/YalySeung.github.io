---

title: "Bridge Pattern"
excerpt: "구현과 추상화 부분까지 독립적 분리!" 

categories:
  - Design Pattern

tags:
  - [Design Pattern]

last_modified_at: 2021-08-27T08:00:00-10:00:00
---


### 개요
 - 추상화 개념과 구현을 분리시켜 독립인 변화를 필요로 할 때 사용하는 디자인 패턴

---

### 구성도
　　![image](/assets/images/DesignPattern/BridgePattern.png){: width="70%" height="70%"}  

 - #### Explain
   - <span style="color:red">Abstraction Class</span> : 구현과 추상화 부분을 독립적으로 분리할 Class
     - implementor : 구현 객체
     - AbstractFunction() : 구현객체를 사용할 메서드  

   - <span style="color:red">AbstractionImpl Class</span> : Abstraction을 구체화한 Class
     - AbstractFunction() : 구현객체를 사용할 메서드  

   - <span style="color:red">Implementor Class</span> : 구현 Class
     - AbstractFunction() : 구현 Class 의 메서드  

   - <span style="color:red">AbstractionImpl Class</span> : Abstraction을 구체화한 Class
     - AbstractFunction() : 구현 Class 의 메서드

　　![image](/assets/images/common/Arrow.png){: width="10%" height="10%"} 구현 부분과 추상화 부분을 각각 확장할 수 있다.
   
---
### 구현방법
 - 패턴을 적용할 클래스를 구현부분과 추상화부분으로 분리
 - 추상화 부분은 상속을 받아서 확장
 - 구현 부분은 새로운 Interface를 정의하고 생성 객체를 위임하는 방식으로 확장
