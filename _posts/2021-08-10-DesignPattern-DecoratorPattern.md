---
title: "Decorator Pattern"
excerpt: "Decorator" 

categories:
  - Design Pattern

tags:
  - [Design Pattern]

last_modified_at: 2021-08-1-T08:06:00-05:00
---


### 개요
 - 객체에 추가적인 요건을 동적으로 추가 하는 디자인 패턴
 - 구조적으로 new 키워드의 사용이 많음
 - 클래스는 확장에 열려있어야 하고 코드 변경에는 닫혀있어야 한다.(OCP : Open-Close Principle)

---

### 구성도

---
### 구현방법
 - SuperClass를 상속받은 <Span style="color:red">ConcreteA</Span>  클래스를 확장하기 위해 SuperClass를 상속받은 <Span style="color:purple">DecorateA</Span> 클래스를 정의
 - <Span style="color:purple">DecorateA</Span> 클래스를 상속받은 <Span style="color:blue">ConcreteDecorateA</Span> 클래스를 정의
 - <Span style="color:blue">ConcreteDecorateA</Span> 클래스에 <Span style="color:red">ConcreteA</Span> 클래스를 위임
 - <Span style="color:purple">DecorateA</Span>의 <Span style="color:purple">MethodA</Span>를 호출하면 <Span style="color:blue">ConcreteDecorateA</Span> 클래스의 <Span style="color:blue">MethodA</Span>가 호출됨, <Span style="color:red">ConcreteA</Span> 클래스의 <Span style="color:red">MethodA</Span> 호출결과와 <Span style="color:blue">ConcreteDecorateA</Span> 의 행위 리턴값이 반환되도록 구성
