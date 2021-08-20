---

title: "TemplateMethod Pattern"
excerpt: "TemplateMethod" 

categories:
  - Design Pattern

tags:
  - [Design Pattern]

last_modified_at: 2021-08-20T08:00:00-10:00:00
---


### 개요
 - 알고리즘의 골격을 정의하여 사용하는 디자인 패턴

---

### 구성도
　　![image](/assets/images/DesignPattern/TemplateMethodPattern.png){: width="70%" height="70%"}  

 - #### Explain
   - <span style="color:red">Abstract Class</span> : 공통된 알고리즘을 정의해 놓은 클래스  
     - templateMethod : 공통 Method
     - primitiveMethod1(), primitiveMethod2() : 재정의 Method
     

   - <span style="color:red">Concrete Class</span> : 필요한 메서드만 재정의 한 클래스  
   

---
### 구현방법
 - <span style="color:blue">Abstract Class</span>에 공통 기능들을 정의
 - <span style="color:red">Concrete Class</span>에 재정의가 필요한 Method들을 Override
