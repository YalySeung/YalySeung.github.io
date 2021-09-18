---

title: "Iterator Pattern"
excerpt: "집합체의 원소 Handling" 

categories:
  - Design Pattern

tags:
  - [Design Pattern]

toc: true
toc_sticky: true
toc_label: "Iterator"

last_modified_at: 2021-09-18T08:00:00-10:00:00
---


# 개요
 - 집합체의 구성을 노출시키지 않고 모든 원소에 접근 가능한 방법 제공

---

# 구성도
  ![image](/assets/images/DesignPattern/IteratorPattern.png){: width="50%" height="50%"}  

 - ## Explain
   - <span style="color:red">Aggregate Interface</span> : 집합체 Interface
     - CreateIterator() : 반복자 생성
   - <span style="color:red">ContreteAggregate Class</span> : 집합체 구현 Class
     - CreateIterator() : 반복자 생성
   - <span style="color:red">Iterator Interface</span> : 반복자 Interface
     - HasNext() : 다음 원소가 있는지 확인하는 메서드
     - Next() : 다음 원소 가져오는 메서드
     - Remove() : 해당 원소 제거하는 메서드
   - <span style="color:red">ConcreteIterator Class</span> : 반복자 구현 Class
     - HasNext() : 다음 원소가 있는지 확인하는 메서드
     - Next() : 다음 원소 가져오는 메서드
     - Remove() : 해당 원소 제거하는 메서드
   
---

# 구현방법
 - 집합체의 원소를 순회하는 Iterator 생성 Method를 구현
 - 반복자에 원소 순회에 필요한 HasNext(), Next(), Remove() 기능을 구현
