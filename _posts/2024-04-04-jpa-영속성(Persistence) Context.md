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
  
## 정의
> **영속성(Persistence) Context란?**  
>
> Server side와 Database 사이에 Entity를 저장하는 논리적인 영역으로 Entity를 보관하고 관리하는 역할을 수행 
{: .notice--info}  
  
![image](../../assets/images/PersistenceContext.png)
  
## 특징
- 영속성 컨텍스트는 Entity Manager를 생성할 때, 하나 생성됨
- Entity Manager를 사용하면 영속성 컨텍스트에 접근 할 수 있으며, 영속성 컨텍스트를 관리할 수 있음
  
## 장점
  
### 1차 Cache 역할
- 영속성 컨텍스트는 Entity를 Map 객체로 저장하여 관리
- 한 가지 기능을 2개의 트랜잭션으로 처리할 경우 영속성 컨텍스트 데이터를 공유함
  
### 동일성 보장
- 같은 객체 정보에 대한 Request가 오면, 동일한 Response를 반환한다.
  
### Transaction 쓰기 지연
- 영속성 Context는 Transaction 범위 안에서 동작
- Transaction 종료 후 Commit이 이루어짐
  
### Lazy Loading
- Entity끼리 관계가 맺어져 있다면 성능저하의 원인이 될 수 있음

---
  
# 연결문서
- [영속성(Persistence)](../../servercommon/servercommon-영속성(Persistence))
- [JPA](../../jpa/jpa-JPA)
- [Cache](../../developcommon/developcommon-Cache)
- [@Transactional](../../annotation/annotation-@Transactional)
- [@Entity](../../jpa/jpa-@Entity)