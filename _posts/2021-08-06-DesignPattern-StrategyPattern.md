---
title: "Strategy Pattern"
excerpt: "기능을 추상화" 

categories:
- Design Pattern

tags:
- [Design Pattern]

toc: true
toc_sticky: true
toc_label: "Strategy Pattern"

last_modified_at: 2022-07-14T08:00:00-10:00:00
---

# 개요
  - 기능을 추상화하여 각각을 캡슐화 하는 디자인 패턴
  - 구현이 아닌 인터페이스에 의존
  - 상속보다는 [구성](#용어설명)을 활용

---

# 구성도

  ![image](/assets/images/DesignPattern/StrategyPattern.png){: width="70%" height="70%"}  

  - ## Explain
    - <span style="color:red">SuperClass</span> : 내가 구현할 Class
      - SetVariance() : 변경되는 기능 인터페이스를 SuperClass에 위임
      - DoVariance() : 변경되는 기능의 DoSomething() 메서드를 호출
    - <span style="color:red">VarianceInterface</span> : 변경되는 기능에 대한 정의 Interface
      - DoSomething() : 수행할 동작
    - <span style="color:red">VarianceImpl</span> : 변경되는 기능을 구체화한 Implement Class

---

# 구현방법
  - 기능알고리즘을 인터페이스로 분리
  - 인터페이스를 상속하는 알고리즘군 구현
  - 수퍼 클래스 로컬 변수를 Set하는 Method, 실행하는 Method 명시

---

# 용어설명
  - 구성 : 클래스에서 사용할 객체를 클래스 변수로 가져와 사용
  - A는 B를 가진다 개념
