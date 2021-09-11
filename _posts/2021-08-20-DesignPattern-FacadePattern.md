---

title: "Facade Pattern"
excerpt: "인터페이스 군을 아우르기" 

categories:
  - Design Pattern

tags:
  - [Design Pattern]

toc: true
toc_sticky: true
toc_label: "Facade Pattern"

last_modified_at: 2021-09-11T08:00:00-10:00:00
---

# 개요
  - 어떤 서브시스템의 인터페이스들에 대한 통합 인터페이스를 제공하는 디자인 패턴

---

# 구성도
  ![image](/assets/images/DesignPattern/FacadePattern.png){: width="70%" height="70%"}  

  - ## Explain
    - <span style="color:red">Client</span> : 사용자
    - <span style="color:red">Facade</span> : 통합 인터페이스  
    - <span style="color:red">Sub System</span> : 인터페이스들의 집합체  
    - <span style="color:red">Interface1, Interface2, Interface3 ...</span> : 서브 시스템의 기능들을 나타내는 인터페이스

---
# 구현방법
  - Sub System을 구성하는 각각의 <span style="color:blue">Interface</span>들을 정의
  - <span style="color:red">Client</span>가 필요로 하는 기능을 <span style="color:Green">Facade</span> 클래스에 구현 => 이때 서브시스템의 Interface 사용
