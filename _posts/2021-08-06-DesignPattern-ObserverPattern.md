---
title: "Observer Pattern"
excerpt: "Observer" 

categories:
  - Design Pattern

tags:
  - [Design Pattern]

last_modified_at: 2021-08-06T08:06:00-05:00
---


### 개요
 - 한 객체의 상태가 바뀌면 그 객체에 의존하는 다른 객체들에게 통보하는 디자인 패턴
 - 서로 상호작용하는 객체들은 느슨한 결합 필요

---

### 구성도

---
### 구현방법
 - Subject(변경되는 주체)와 Ovserver(주체의 변경을 감시하는 개체)로 구성
 - Subject는 Observer들을 등록, 삭제 하는 메서드와 변경을 통보하는 메서드 필요
 - Observer 인터페이스를 상속한 객체들은 update(subject가 변경되면 수행할 행동) 메서드 구현 

---
### 용어설명
