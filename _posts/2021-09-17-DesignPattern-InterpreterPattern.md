---

title: "Interpreter Pattern"
excerpt: "문법적 언어를 해석" 

categories:
  - Design Pattern

tags:
  - [Design Pattern]

toc: true
toc_sticky: true
toc_label: "Set"

last_modified_at: 2021-09-17T08:00:00-10:00:00
---


# 개요
 - 문법 규칙을 캡슐화 한 디자인 패턴
 - 테스트 툴을 만들어 사용해야 할 경우 적용 할 수 있는 패턴

---

# 구성도
  ![image](/assets/images/DesignPattern/InterpreterPattern.png){: width="50%" height="50%"}  

 - ## Explain
   - <span style="color:red">Interpreter Class</span> : Expression을 사용하여, 문법적 언어를 해석하는 Class
   - <span style="color:red">Expression Interface</span> : 표현식 Interface
     - Interprete() : 언어를 해석하는 함수
   - <span style="color:red">TerminalExpression Class</span> : Terminal Data를 해석하는 Expression Class
     - data : 해석할 Terminal data
     - Interprete() : 언어를 해석하는 함수
   - <span style="color:red">NonTerminalExpression Class</span> : 표현식 간의 상호작용 Expression Class
     - expressionA : 표현식A
     - expressionA : 표현식B
     - Interprete() : 언어를 해석하는 함수
   
---

# 구현방법
 - 해석 할 syntax 들 정의
 - 각 syntax 별 Expression Interface를 구현한 Class 생성
 - syntax 별 해석 로직을 Interprete에 정의
