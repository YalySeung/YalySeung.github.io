---
title : "Querydsl InlineView"
excerpt : "Querydsl InlineView"
toc : true
toc_sticky : true
toc_label : "Querydsl InlineView"
categories:
- JPA
tags:
- [Querydsl, Spring, JPA]
last_modified_at: 2024-05-10T08:00:00-10:00:00
---
  
---
  
> **Querydsl Inline View란?**  
>
>  Querydsl에서 **서브쿼리를 활용하여 특정 데이터 집합을 임시 뷰로 사용하는 방법**을 의미한다. 
{: .notice--info}  

  Querydsl에서는 **Inline View(인라인 뷰)를 활용하여 복잡한 쿼리를 효율적으로 작성할 수 있으며, 서브쿼리를 엔티티와 결합하여 성능을 최적화할 수 있다.**  
  
## 사용법
  
### 1️⃣ 기본적인 Querydsl Inline View 예제
  
```java
JPAQuery<?> inlineView = queryFactory  
    .select(qOrder.userId, qOrder.totalPrice.sum())  
    .from(qOrder)  
    .groupBy(qOrder.userId);  

List<User> users = queryFactory.selectFrom(qUser)  
    .where(qUser.id.in(inlineView))  
    .fetch();
```

---
  
## 인라인 뷰 사례별 예시
  
### 2️⃣ 특정 조건을 가진 집계 데이터를 서브쿼리로 활용
  
```java
QOrder qOrderSub = new QOrder("orderSub");

JPAQuery<?> inlineView = queryFactory  
    .select(qOrderSub.userId, qOrderSub.totalPrice.sum())  
    .from(qOrderSub)  
    .where(qOrderSub.status.eq("COMPLETED"))  
    .groupBy(qOrderSub.userId);

List<User> users = queryFactory.selectFrom(qUser)  
    .where(qUser.id.in(inlineView))  
    .fetch();
```
  
### 3️⃣ 최신 주문만 조회하는 인라인 뷰 적용
  
```java
QOrder qOrderSub = new QOrder("orderSub");

JPAQuery<?> inlineView = queryFactory  
    .select(qOrderSub.userId, qOrderSub.orderDate.max())  
    .from(qOrderSub)  
    .groupBy(qOrderSub.userId);

List<Order> latestOrders = queryFactory.selectFrom(qOrder)  
    .where(qOrder.orderDate.in(inlineView))  
    .fetch();
```
  
### 4️⃣ 특정 기간 내의 데이터만 필터링하는 인라인 뷰 활용
  
```java
QOrder qOrderSub = new QOrder("orderSub");

JPAQuery<?> inlineView = queryFactory  
    .select(qOrderSub.userId, qOrderSub.totalPrice.sum())  
    .from(qOrderSub)  
    .where(qOrderSub.orderDate.between(startDate, endDate))  
    .groupBy(qOrderSub.userId);

List<User> filteredUsers = queryFactory.selectFrom(qUser)  
    .where(qUser.id.in(inlineView))  
    .fetch();
```
  
### 5️⃣ JOIN과 함께 인라인 뷰 적용
  
```java
QOrder qOrderSub = new QOrder("orderSub");

JPAQuery<?> inlineView = queryFactory  
    .select(qOrderSub.userId, qOrderSub.totalPrice.sum())  
    .from(qOrderSub)  
    .groupBy(qOrderSub.userId);

List<User> usersWithOrders = queryFactory.selectFrom(qUser)  
    .join(inlineView).on(qUser.id.eq(qOrderSub.userId))  
    .fetch();
```

---
  
## 장점과 단점
  
### ✅ 장점
- **SQL 서브쿼리를 활용하여 보다 직관적인 코드 작성 가능**  
- **복잡한 조회 로직을 간결하게 구현할 수 있음**  
- **조건별 데이터 필터링을 손쉽게 적용 가능**  
  
### ❌ 단점
- **일부 데이터베이스에서는 서브쿼리 성능 저하 가능**  
- **JPA 표준이 아니라 Querydsl에 종속됨**  

---
  
# 연결문서
