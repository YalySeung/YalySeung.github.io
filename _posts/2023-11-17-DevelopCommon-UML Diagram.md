---
title : "UML Diagram"
excerpt : "UML Diagram"
toc : true
toc_sticky : true
toc_label : "UML Diagram"
categories:
- DevelopCommon
tags:
- [DevelopCommon]
last_modified_at: 2023-11-17T08:00:00-10:00:00
---

# 날짜 : 2023-11-17 10:14

# 태그 : #DevelopCommon
---

# 내용

## 정의
> UML Diagram이란?
>Unified Modeling Language
>통합 모델링 언어를 사용하여 시스템 상호작용, 업무흐름, 시스템구조, 컴포넌트 관계 등을 그린 도면

## 분류

### 구조 다이어그램(Structure Diagram)
> 구조 다이어그램이란?
> 각 요소들의 정적은 면을 보기 위한 다이어그램
> 시스템 개념, 관계 등의 측면에서 표현

### 행위 다이어그램(Behavior Diagram)
> 행위 다이어그램이란?
> 요소들의 동적인 면을 보기 위한 다이어그램
> 시퀀셜한 표현을 위한 다이어그램

## 종류

| Diagram 명            | 용도                                                 |
| ------------------------ | ---------------------------------------------------- |
| Activity Diagram      | 업무의 흐름을 모델링하거나 객체의 생명주기를 표현    |
| Class Diagram         | 시스템의 구조적인 모습 묘사                          |
| Collaboration Diagram | 객체와 객체가 주고받는 메시지 중심으로 묘사          |
| Component Diagram     | 소프트웨어 구조를 묘사                               |
| Deployment Diagram    | 기업환경의 구성과 컴포넌트들 간의 관계 묘사          |
| Sequence Diagram      | 객체 간의 메시지 전달을 시간적 흐름에서 분석함       |
| Use Case Diagram      | 요구사항 분석 과정에서 시스템 외부와 상호작용을 묘사 |

## Class Diagram

### Class Relationship
- 게임을 예시로 각 관계에 대해 이해해보자
  
![image](./../../assets/images/GameExampleOfUML.png)

#### 일반화(Generalization)
- 부모클래스와 자식클래스간 상속 관계를 나타냄
- 부모는 자식을 **일반화(Generalize)**, 자식을 부모를 **구체화(Specialize)**
- 속이 빈 화살표로 표현
- 위 예시에서 Weapon과 Item 의 관계에 해당한다.
  
![image](./../../assets/images/Generalize.png)

```java
public abstract class Item {  
    String name;  
  
    public String getInfo(){  
        return name;  
    }  
}

public class Weapon extends Item {  
    String name = "weapon";  
    String type = "Sword";  
    @Override  
    public String getInfo(){  
        return "name : " + name + ", type : " + type;  
    }  
}
```

#### 실체화(Realization)
- interface의 기능을 실제로 구현
- 점선에 속이 빈 화살표로 표현
- 위 예시에서 Attackable, Damagable 과 Monster의 관계에 해당한다.
  
![image](./../../assets/images/Realization.png)

```java
public interface Attackable {  
    public void attack();  
}

public interface Damagable {  
    public void Damanage(DamangeInfo damangeInfo);  
}

public class Monster implements Attackable, Damagable {  
    Status status;  
  
    public Monster() {  
        status = new Status(100, 100);  
    }  
  
    @Override  
    public void attack() {  
        System.out.print("때린다!!");  
    }  
  
    @Override  
    public void Damanage(DamangeInfo damangeInfo) {  
        status.setHp(status.getHp() - damangeInfo.damage);  
    }  
}
```

#### 의존(Dependency)
- 일시적이고 느슨한 참조 관계
- 멤버변수로 다른 객체를 사용할 때
- 점선 화살표로 표현
- 위 예시에서 Damabable, Monster와 DamageInfo의 관계에 해당한다.
  
![image](./../../assets/images/Dependency.png)

```java
public class DamangeInfo {  
    public int damage;  
    public String type;  
}

public interface Damagable {  
    public void Damanage(DamangeInfo damangeInfo);  
}

public class Monster implements Attackable, Damagable {  
    Status status;  
  
    public Monster() {  
        status = new Status(100, 100);  
    }  
  
    @Override  
    public void attack() {  
        System.out.print("때린다!!");  
    }  
  
    @Override  
    public void Damanage(DamangeInfo damangeInfo) {  
        status.setHp(status.getHp() - damangeInfo.damage);  
    }  
}
```

#### 집약(Aggregation)
- 한 객체가 다른 객체를 포함하는 더 큰 개념
- 두 객체는 독립적이며, 라이프사이클이 독립적
- 속이 빈 다이아몬드 실선으로 표현
- 뒤 예시에서 MonsterAdministrator와 Monster의 관계에 해당한다.
  
![image](./../../assets/images/Aggregation.png)

```java
public class Monster implements Attackable, Damagable {  
    Status status;  
  
    public Monster() {  
        status = new Status(100, 100);  
    }  
  
    @Override  
    public void attack() {  
        System.out.print("때린다!!");  
    }  
  
    @Override  
    public void Damanage(DamangeInfo damangeInfo) {  
        status.setHp(status.getHp() - damangeInfo.damage);  
    }  
}

public class MonsterAdministrator {  
    private List<Monster> monsterList;  
}
```

#### 연관(Association)
- 일반적으로 두 객체 간에 어떤 형태의 관계가 있는지만 표시
- 라이프사이클이 독립적
- 실선으로 표현
- 위 예시에서 GameManager와 MonsterAdministrator의 관계에 해당
  
![image](./../../assets/images/Association.png)

```java
public class MonsterAdministrator {  
    private List<Monster> monsterList;  
}

public class GameManager {  
    MonsterAdministrator monsterAdministrator;  
}
```

#### 합성(Composition)
- [집약(Aggregation)](#집약(aggregation)) 이나 [집약(Aggregation)](#집약(aggregation)) 보다 더 강력한 결합 관계
- 한 객체가 다른 객체를 포함하며, 라이프사이클 공유
- 속이 찬 다이아몬드 실선으로 표현
- 위 예시에서 Status와 Monster의 관계에 해당한다.
  
![image](./../../assets/images/Composition.png)

```java
public class Status {  
    int hp;  
    int mp;  
  
    public Status(int hp, int mp) {  
        this.hp = hp;  
        this.mp = mp;  
    }  
  
    public int getHp() {  
        return hp;  
    }  
  
    public void setHp(int hp) {  
        this.hp = hp;  
    }  
  
    public int getMp() {  
        return mp;  
    }  
  
    public void setMp(int mp) {  
        this.mp = mp;  
    }   
}

public class Monster implements Attackable, Damagable {  
    Status status;  
  
    public Monster() {  
        status = new Status(100, 100);  
    }  
  
    @Override  
    public void attack() {  
        System.out.print("때린다!!");  
    }  
  
    @Override  
    public void Damanage(DamangeInfo damangeInfo) {  
        status.setHp(status.getHp() - damangeInfo.damage);  
    }  
}
```

---

# 연결문서