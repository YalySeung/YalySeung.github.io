---
title: "Flyweight Pattern"
excerpt: "공유를 통해 대량의 객체를 지원"

categories:
  - Design Pattern

tags:
  - [Design Pattern]

toc: true
toc_sticky: true
toc_label: "Flyweight"

last_modified_at: 2021-09-27T08:00:00-10:00:00
---


# 개요
 - 어플리케이션에서 생성되는 객체의 수가 많을 경우 미리 생성해 놓은 객체를 사용
 - 미리 생성해 놓은 객체가 없을 경우 새로운 객체 생성
 - 불필요한 객체 생성을 줄일 수 있음

---

# 구성도
  ![image](/assets/images/DesignPattern/FlyweightPattern.png){: width="60%" height="60%"}  

 - ## Explain
   - <span style="color:red">FlyweightFactory Class</span> : Flyweight 객체를 관리하는 Factory
     - flyweightCollection : Flyweight 객체 List
     - GetFlyweight() : Flyweight 객체를 반환하는 public 메서드
   - <span style="color:red">Flyweight Class</span> : 대량 생산이 필요한 객체의 Interface
     - DoSomething() : 행위 Method
   - <span style="color:red">ConcreteFlyweightA Class</span> : Flyweight 구현 Class
     - DoSomething() : 행위 Method
   - <span style="color:red">ConcreteFlyweightB Class</span> : Flyweight 구현 Class
     - DoSomething() : 행위 Method
   
---

# 구현방법
 - 대량 생산이 필요한 객체의 <span style="color:blue">Interface</span>를 정의
 - <span style="color:blue">Interface</span> 구현
 - 구현한 Class를 생성하는 <span style="color:yellow">Factory Class</span>를 정의
 - <span style="color:yellow">Factory Class</span>에 Flyweight 객체를 관리하는 Collection 정의
 - <span style="color:yellow">Factory Class</span>에 Flyweight 객체를 반환하는 GetFlyweight() 메서드를 정의 -> Collection에 객체가 없을 경우 객체 생성