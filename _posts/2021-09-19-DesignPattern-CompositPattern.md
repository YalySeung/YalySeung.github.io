---
title: "Composit Pattern"
excerpt: "부분과 전체" 

categories:
  - Design Pattern

tags:
  - [Design Pattern]

toc: true
toc_sticky: true
toc_label: "Composit"

last_modified_at: 2021-09-19T08:00:00-10:00:00
---


# 개요
 - 객체들을 트리 구조로 구성
 - 부분과 전체를 나타내는 계층구조
 - 단일역할 원칙에 위배 -> child 관리, operation 2가지 역할
 - Leaf와 Component를 같은 방식으로 처리하여 투명성을 확보할 수 있다는 장점

---

# 구성도
  ![image](/assets/images/DesignPattern/CompositPattern.png){: width="60%" height="60%"}  

 - ## Explain
   - <span style="color:red">Component Class</span> : 컴포넌트 추상 Class
     - Operation() : Class의 행위 메서드
     - AddComponent() : Child Component를 추가하는 메서드
     - RemoveComponent() : Child Component를 제거하는 메서드
     - GetChildComponent() : Child Component를 가져오는 메서드
   - <span style="color:red">Composit Class</span> : Child를 가지고 있는 컴포넌트 구현 Class
     - Operation() : Class의 행위 메서드
     - AddComponent() : Child Component를 추가하는 메서드
     - RemoveComponent() : Child Component를 제거하는 메서드
     - GetChildComponent() : Child Component를 가져오는 메서드
   - <span style="color:red">Leaf Class</span> : Child를 가지고 있지 않은 컴포넌트 구현 Class
     - Operation() : Class의 행위 메서드
   
---

# 구현방법
 - 각 객체를 행위만 하는 객체 / parent-child 구조를 갖는 객체로 구분
 - 각 클래스의 행위를 정의
 - AddComponent 메서드를 활용하여, parent-child 구조로 각 객체를 연결
