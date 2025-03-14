---
title : "JPQLQuery"
excerpt : "JPQLQuery"
toc : true
toc_sticky : true
toc_label : "JPQLQuery"
categories:
- JPA
tags:
- [Spring, JPA, Querydsl]
last_modified_at: 2024-05-21T08:00:00-10:00:00
---
  
---
  
> **JPQLQuery란?**  
>
>  JPA에서 엔티티 객체를 대상으로 SQL과 유사한 쿼리를 실행하는 방법을 의미한다. 
{: .notice--info}  

  JPQL(Java Persistence Query Language)은 **테이블이 아닌 엔티티 객체를 대상으로 질의하는 객체 지향 쿼리 언어**이다.  
  SQL과 문법이 유사하지만, **JPQL은 데이터베이스가 아닌 엔티티 객체를 기준으로 작성된다.**
  
## JPQL 기본 문법
  
### 1️⃣ SELECT 예제
  
```java
@Query("SELECT u FROM User u WHERE u.status = 'ACTIVE'")
List<User> findActiveUsers();
```
  
### 2️⃣ WHERE 절 사용
  
```java
@Query("SELECT u FROM User u WHERE u.name = :name")
User findByName(@Param("name") String name);
```
  
### 3️⃣ JOIN을 활용한 JPQL
  
```java
@Query("SELECT o FROM Order o JOIN o.user u WHERE u.id = :userId")
List<Order> findOrdersByUserId(@Param("userId") Long userId);
```
  
## JPQL과 SQL 비교
  
| 구분 | JPQL | SQL |
|------|------|------|
| 대상 | 엔티티 객체 | 데이터베이스 테이블 |
| 컬럼명 | 필드명 사용 | 실제 테이블 컬럼명 |
| JOIN | 연관 관계 기반 | 직접 JOIN 수행 |
  
## 장점과 단점
  
### ✅ 장점
- **데이터베이스에 독립적인 쿼리 작성 가능**  
- **객체 지향적 접근 방식으로 유지보수 용이**  
  
### ❌ 단점
- **SQL보다 실행 성능이 낮을 수 있음**  
- **복잡한 쿼리는 네이티브 SQL이 필요할 수도 있음**  

---
  
# 연결문서
- [JPA](../../jpa/jpa-JPA)
- [Querydsl](../../jpa/jpa-Querydsl)
