---
title : "영속성(Persistence) Context"
excerpt : "영속성(Persistence) Context"
toc : true
toc_sticky : true
toc_label : "영속성(Persistence) Context"
categories:
- JPA
tags:
- [Database, Spring, JPA]
last_modified_at: 2024-04-04T08:00:00-10:00:00
---
  
---
  
> **영속성(Persistence) Context란?**  
>
> Server side와 Database 사이에 Entity를 저장하는 논리적인 영역으로 Entity의 생명주기를 관리하는 메모리상의 환경이다. 
{: .notice--info}  

  영속성 컨텍스트는 실제 DB의 데이터를 접근하기 전 일종의 캐시 역할을 한다고 보면 된다. [EntityManager](../../jpa/jpa-EntityManager)에 의해 관리되며, JPA 표준에서의 **영속성 컨텍스트는 하나의 EntityManager 인스턴스에 연관**된다. 이 메모리상의 컨텍스트는 애플리케이션과 데이터베이스 간의 효율적 데이터 처리를 가능하게 한다.
  
![image](../../assets/images/PersistenceContext.png)

  영속성 컨텍스트를 사용함으로써, 얻을 수 있는 장점을 자세히 알아보자. 

  첫째, 영속성 컨텍스트는 Entity를 Map 객체로 관리하여, 2개의 트랜잭션에서 동시에 접근 할 경우 데이터를 공유할 수 있는 **1차 Cache 역할**을 수행한다.  
  둘째, 영속성 컨텍스트 내에서 동일한 키로 관리되는 엔티티는 항상 동일한 인스턴스로 유지되는 **동일성을 보장**한다.  
  셋째, 영속성 컨텍스트는 트랜잭션 범위 안에서 동작하며, **트랜잭션이 종료돼야 Commit을 수행(쓰기 지연)**한다.
  
## Entity의 상태
  영속성 컨텍스트 상의 엔티티 객체는 네 가지 상태를 가진다.

  new로 생성된 객체는 단순한 자바 객체이며, 영속성 컨텍스트와는 무관한 **비영속 상태(Transient)**이다. 
  
```java
Member member = new Member();
```

  EntityManager에 등록되면, **영속 상태(Persistent)**가 되어 1차 캐시(메모리)에 저장 된다. 변경사항은 트랜잭션 종료 후 DB에 반영된다.
  
```java
entityManager.persist(member);
```

  detach(), clear(), close() 를 호출하면, 영속성 컨텍스트가 더 이상 엔티티를 관리하지 않는 **준영속 상태(Detached)**로 전환된다.
  
```java
entityManager.detach(member);
```

  remove() 를 호출하면, 엔티티 삭제가 예약되는 **삭제 상태**에 접어든다. remove() 메서드를 호출한 엔티티는 DB에서 삭제되지만, commit 전에 rollback 할 수 있다.
  
```java
entityManager.remove(member);
```

---
  
# 연결문서
- [영속성(Persistence)](../../servercommon/servercommon-영속성(Persistence))
- [JPA](../../jpa/jpa-JPA)
- [Cache](../../developcommon/developcommon-Cache)
- [@Transactional](../../annotation/annotation-@Transactional)
- [@Entity](../../jpa/jpa-@Entity)
- [EntityManager](../../jpa/jpa-EntityManager)
