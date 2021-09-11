---

title: "Builder Pattern"
excerpt: "복합객체 생성을 캡슐화" 

categories:
  - Design Pattern

tags:
  - [Design Pattern]

toc: true
toc_sticky: true
toc_label: "Builder Pattern"

last_modified_at: 2021-09-11T08:00:00-10:00:00
---

# 개요
  - 제품을 여러 단계에 나누어 만들 수 있도록 제품 단계를 캡슐화
  - 제품 내부 구조 보호

---

# 구성도
  ![image](/assets/images/DesignPattern/BuilderPattern.png){: width="70%" height="70%"}  

  - ## Explain
    - <span style="color:red">Client Class</span> : Builder에 객체를 요청하는 사용자 Class
    - <span style="color:red">AbstractBuilder Class</span> : Builder 부모 Class
      - buildResult : 결과 객체
      - GetObect() : 결과 객체를 반환
      - BuildA(), BuildB() : 객체의 특성을 만드는 Method
    - <span style="color:red">ConcreteBuilder Class</span> : 구현 Class
      - BuildA(), BuildB() : 객체의 특성을 만드는 Method

---

# 구현방법
  - 생성할 객체가 가질 수 있는 특성을 각각 BuildA(), BuildB().. 로 정의
  - Client는 Builder에서 필요한 특성에 해당하는 Method를 호출, Builder에게 객체 반환 요청하여 사용
