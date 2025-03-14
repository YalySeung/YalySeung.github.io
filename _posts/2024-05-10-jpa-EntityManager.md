---
title : "EntityManager"
excerpt : "EntityManager"
toc : true
toc_sticky : true
toc_label : "EntityManager"
categories:
- JPA
tags:
- [Spring, JPA]
last_modified_at: 2024-05-10T08:00:00-10:00:00
---
  
---
  
## 주요 메서드
  
| 메서드           | 역할                          | 데이터베이스 동기화 여부 | 영속성 컨텍스트 상태      |
| ------------- | --------------------------- | ------------- | ---------------- |
| **persist()** | 엔터티를 영속성 컨텍스트에 저장           | X             | 관리 상태 (managed)  |
| **flush()**   | 영속성 컨텍스트의 변경 사항을 데이터베이스에 반영 | O             | 유지               |
| **clear()**   | 영속성 컨텍스트 초기화 및 관리 중인 엔터티 제거 | X             | 비관리 상태(detached) |
  
## Repository에서 EntityManager 사용
  `EntityManager`를 주입하여 사용하는 방식에는 2가지가 있다. `@Autowired`를 사용하는 방식과 `@PersistenceContext`를 사용하는 방식이다.
  
### 1️⃣ `@Autowired`를 이용한 방식
  
```java
@Autowired
EntityManager entityManager;
```
  위 방식은 트랜잭션과 관련된 문제가 발생할 수 있기 때문에 권장되지 않는다.
  
### 2️⃣ `@PersistenceContext`를 이용한 방식 (권장)
  
```java
@PersistenceContext
EntityManager entityManager;
```
  `@PersistenceContext`를 통해 `EntityManager`를 주입할 경우 **JPA 환경과의 통합을 보장**하며, JPA 트랜잭션 내에서 자동으로 연결되고 관리된다.  
  이 방식이 **JPA 관련 코드에 대해 일관성을 유지**할 수 있으며, **트랜잭션 관리에 안전**하기 때문에 권장된다.

---
  
# 연결문서
