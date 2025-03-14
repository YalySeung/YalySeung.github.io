---
title : "BooleanExpression"
excerpt : "BooleanExpression"
toc : true
toc_sticky : true
toc_label : "BooleanExpression"
categories:
- JPA
tags:
- [Spring, JPA, Querydsl]
last_modified_at: 2024-04-22T08:00:00-10:00:00
---
  
---
  
> **BooleanExpression이란?**  
>
> Querydsl Where 조건절에 조건으로 사용되는 Class이다. 
{: .notice--info}  
  
## BooleanExpression 개요
 Querydsl에서 `BooleanExpression`은 **동적 쿼리 조건을 조합할 때 사용되는 클래스**로, `where()` 절에 조건을 추가할 때 활용된다.
  
## BooleanExpression 활용
  
### 1️⃣ 기본적인 BooleanExpression 사용
 `BooleanExpression`을 활용하면 `null` 체크를 통해 조건을 동적으로 추가할 수 있다.
  
```java
import com.querydsl.core.types.dsl.BooleanExpression;
import static com.myproject.domain.QUser.user;

public BooleanExpression isActive(Boolean isActive) {
    return isActive != null ? user.active.eq(isActive) : null;
}
```
  
### 2️⃣ 여러 BooleanExpression 조합
 `BooleanExpression`을 활용하면 여러 조건을 조합하여 동적 쿼리를 구성할 수 있다.
  
```java
public BooleanExpression hasName(String name) {
    return name != null ? user.name.eq(name) : null;
}

public BooleanExpression isOlderThan(Integer age) {
    return age != null ? user.age.gt(age) : null;
}

public BooleanExpression buildQuery(String name, Integer age) {
    return hasName(name).and(isOlderThan(age));
}
```
  
## BooleanExpression과 BooleanBuilder 비교
 `BooleanBuilder`와 `BooleanExpression`은 동적 조건을 만들 때 사용되지만, 주요 차이점이 있다.

| 특징              | BooleanExpression | BooleanBuilder |
|-----------------|-----------------|----------------|
| 타입            | `BooleanExpression` | `BooleanBuilder` |
| 조합 방식        | `.and()`, `.or()` 사용 | `.and()`로 조건 추가 가능 |
| null 처리      | 직접 `null` 체크 필요 | 자동으로 `null`을 처리 |
| 활용 사례       | 단순한 조건 조합 | 복잡한 다중 조건 처리 |
  
## BooleanExpression의 장점과 단점
  
### ✅ 장점
- Querydsl의 `where()` 절에 직접 적용 가능
- 여러 조건을 손쉽게 조합 가능
- 명확한 타입으로 가독성이 좋음
  
### ❌ 단점
- `null` 체크를 직접 해야 함
- 복잡한 조건을 추가할 경우 `BooleanBuilder`가 더 적합

---
  
# 연결문서
- [BooleanBuilder](../../jpa/jpa-BooleanBuilder)
- [Querydsl](../../jpa/jpa-Querydsl)