---
title: "Decorator Pattern"
excerpt: "요건을 동적으로 추가하기" 

categories:
- Design Pattern

tags:
- [Design Pattern]

toc: true
toc_sticky: true
toc_label: "Decorator Pattern"

last_modified_at: 2022-07-14T08:00:00-10:00:00
---

# 개요
- 객체에 추가적인 요건을 동적으로 추가 하는 디자인 패턴
- 구조적으로 new 키워드의 사용이 많음
- 상속만으로 해결이 안되는 문제에 대한 해결방안
- 클래스는 확장에 열려있어야 하고 코드 변경에는 닫혀있어야 한다.(OCP : Open-Close Principle)

---

# 구성도
  ![image](/assets/images/DesignPattern/DecoratorPattern.png){: width="70%" height="70%"}  

  - ## Explain
    - <span style="color:red">SuperClass</span> : 최상위 Class
      - MethodA() : 확장할 기능  
    - <span style="color:red">ChildClass</span> : SuperClass의 자식 Class
    - <span style="color:red">AbstractDecorator</span> : Decorator Class
    - <span style="color:red">ChildDecorator</span> : 생성자에서 ChildClass를 위임받아 MethodA() 를 확장 하는 실질적인 Decorator 구현 Class

---
# 구현방법
  - SuperClass를 상속받은 <Span style="color:red">ConcreteA</Span>  클래스를 확장하기 위해 SuperClass를 상속받은 <Span style="color:purple">DecorateA</Span> 클래스를 정의
  - <Span style="color:purple">DecorateA</Span> 클래스를 상속받은 <Span style="color:blue">ConcreteDecorateA</Span> 클래스를 정의
  - <Span style="color:blue">ConcreteDecorateA</Span> 클래스에 <Span style="color:red">ConcreteA</Span> 클래스를 위임
  - <Span style="color:purple">DecorateA</Span>의 <Span style="color:purple">MethodA</Span>를 호출하면 <Span style="color:blue">ConcreteDecorateA</Span> 클래스의 <Span style="color:blue">MethodA</Span>가 호출됨, <Span style="color:red">ConcreteA</Span> 클래스의 <Span style="color:red">MethodA</Span> 호출결과와 <Span style="color:blue">ConcreteDecorateA</Span> 의 행위 리턴값이 반환되도록 구성
