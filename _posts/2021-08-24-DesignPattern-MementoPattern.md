---

title: "Memento Pattern"
excerpt: "상태 저장하기" 

categories:
  - Design Pattern

tags:
  - [Design Pattern]

toc: true
toc_sticky: true
toc_label: "Memento Pattern"

last_modified_at: 2021-09-11T08:00:00-10:00:00
---

# 개요
  - 현재 상태를 저장하고 불러오는 디자인 패턴
  - 되돌리기 기능 구현시 사용

---

# 구성도
  ![image](/assets/images/DesignPattern/MementoPattern.png){: width="70%" height="70%"}  

  - ## Explain
    - <span style="color:red">Originator Class</span> : 상태 저장이 필요한 클래스
      - state : 상태 변수
      - CreateMemento() : 상태 저장 메서드
      - RestoreMemento() : 상태 되돌리기 메서드
    - <span style="color:red">Memento Class</span> : 상태 클래스
      - state : 상태 변수
      - SetState() : 상태 저장
      - GetState() : 상태 반환

---

# 구현방법
  - <span style="color:blue">Originator Class</span>에서 자신의 현재 상태를 저장한 Memento 생성
  - <span style="color:blue">Originator Class</span>에 Memento 들을 Stack 데이터 구조로 저장
  - 상태 되돌리가 필요할 경우 <span style="color:red">Memento Class</span>에 GetState() 메서드를 사용
