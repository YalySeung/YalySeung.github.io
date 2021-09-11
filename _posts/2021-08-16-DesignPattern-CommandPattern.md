---
title: "Command Pattern"
excerpt: "명령 부분은 캡슐화" 

categories:
  - Design Pattern

tags:
  - [Design Pattern]

toc: true
toc_sticky: true
toc_label: "Command Pattern"

last_modified_at: 2021-09-11T08:06:00-05:00
---

# 개요
  - 명령을 객체로 캡슐화 하는 디자인 패턴
  - 요청 내역을 객체로 캡슐화, 매개변수화
  - 요청객체와 수행객체 분리

---

# 구성도
  ![image](/assets/images/DesignPattern/CommandPattern.png){: width="70%" height="70%"}  

  - ## Explain
    - <span style="color:red">Client</span> : Invoker에 커맨드 실행을 요청하는 Class
    - <span style="color:red">Invoker</span> : 요청을 캡슐화한 Class
      - commands : 명령들을 담고 있는 리스트
      - SetCommand() : Command 객체를 추가하는 Method
      - ExecuteCommand() : Command를 실행 하는 Method
    - <span style="color:red">Command</span> : 커맨드를 캡슐화한 인터페이스
      - Excute() : 수행
      - Undo() : 수행 되돌리기
    - <span style="color:red">ConcreteCommand</span> : 커맨드를 구체화한 Class
      - Excute() : 수행
      - Undo() : 수행 되돌리기
    - <span style="color:red">Receiver</span> : 실제로 수행을 하는 Class
      - Action() : 실제로 수행하는 Method

---
# 구현방법
  - CommandList를 Set하고 ExcuteCommand의 인수 index에 따라, Command.Execute() Method를 실행할 수 있는 Invoker Class 정의
  - Command 인터페스를 구현
  - Action에 실제 수행할 동작을 정의한 Receiver Class 정의

---
# 용어설명
  - Invoker : 커맨드 실행을 요청하는 개체
  - Receiver : 실제로 동작을 수행하는 개체
