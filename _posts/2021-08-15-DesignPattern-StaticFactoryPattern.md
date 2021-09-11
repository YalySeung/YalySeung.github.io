---

title: "StaticFactory Pattern"
excerpt: "객체를 생성하는 공장" 

categories:
- Design Pattern

tags:
- [Design Pattern]

toc: true
toc_sticky: true
toc_label: "StaticFactory Pattern"

last_modified_at: 2021-09-11T08:06:00-05:00
---

# 개요
- 객체를 생성하는 Static Method를 사용하는 디자인 패턴
- FactoryMethod Pattern의 한 종류

---

# 구성도
  ![image](/assets/images/DesignPattern/StaticFactoryPattern.png){: width="70%" height="70%"}  

  - ## Explain
    - <span style="color:red">ItemFactory</span> : Item 객체를 생성하는 Class
      - static Item Create() : type에 따른 객체 생성 Method
    - <span style="color:red">Item</span> : 생성할 객체의 최상위 Interface
    - <span style="color:red">ItemImpl</span> : 생성할 구현객체

---

# 구현방법
  - Type에 따라 Item을 생성하는 Static Method를 가진 <span style="color:red">Factory</span> 클래스 정의
  - <span style="color:blue">Item</span> 인터페이스를 상속받은 <span style="color:blue">ItemImpl1</span>, <span style="color:blue">ItemImple2</span> .. 클래스 정의
  - <span style="color:red">Factory</span> 클래스의 Static Method에서 Type에 따라 <span style="color:blue">ItemImpl</span> 객체를 return;
