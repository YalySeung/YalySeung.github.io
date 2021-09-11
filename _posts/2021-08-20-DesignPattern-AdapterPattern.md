---

title: "Adapter Pattern"
excerpt: "기존 인터페이스에 적응시키기" 

categories:
  - Design Pattern

tags:
  - [Design Pattern]

toc: true
toc_sticky: true
toc_label: "Adapter Pattern"

last_modified_at: 2021-09-11T08:00:00-10:00:00
---

# 개요
  - 한 클래스의 인터페이스를 클라이언트에서 사용하는 다른 인터페이스로 변환
  - 기존 인터페이스로 새로운 클래스 인터페이스를 Wrapping 

---

# 구성도
  ![image](/assets/images/DesignPattern/AdapterPattern.png){: width="70%" height="70%"}  

  - ## Explain
    - <span style="color:red">Client</span> : 사용자
    - <span style="color:red">Adapter</span> : 기존 인터페이스
    - <span style="color:red">Adaptee</span> : 새로운 인터페이스

---
# 구현방법
  - <span style="color:blue">Adaptee</span>를 위임하는 <span style="color:red">Adapter</span> 정의
  - <span style="color:red">Adapter</span>의 Method에서 <span style="color:blue">Adaptee</span>를 사용한 기능 구현
