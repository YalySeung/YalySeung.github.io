---
title : "BooleanBuilder"
excerpt : "BooleanBuilder"
toc : true
toc_sticky : true
toc_label : "BooleanBuilder"
categories:
- JPA
tags:
- [Spring, JPA, Querydsl]
last_modified_at: 2024-04-22T08:00:00-10:00:00
---
  
---
  
> **BooleanBuilder란?**  
>
>  QueryDSL에서 제공하는 클래스로, 동적으로 조건을 구성하고 조합할 수 있는 기능을 제공한다. 
{: .notice--info}  

  BooleanBuilder의 가장 큰 특징은 **빌더 패턴을 사용하여 조건을 동적으로 조합할 수 있으며, 최종적으로 `BooleanExpression`을 반환한다.**  
  
## 주요 메서드

| 메서드 명    | 기능                                   |
| -------- | ------------------------------------ |
| and      | AND 조건으로 조합한다.                       |
| or       | OR 조건으로 조합한다.                        |
| not      | 부정을 추가한다.                            |
| andAnyOf | AND ( A OR B )                       |
| orAllof  | OR ( A AND B )                       |
| build    | 내부 조건을 조합하여 BooleanExpression을 반환한다. |
  
## andAnyOf(), orAllOf()
  Querydsl에서는 `or` 조건보다 `and`의 우선순위가 높으며, Java 코드에서 괄호로 묶어도 우선순위가 변하지 않는다.  
  따라서 `and(A or B)`와 같은 조건을 처리하려면 `andAnyOf()`를 사용해야 한다.
  
### 1️⃣ 예제 - SQL 변환
  
```sql
SELECT *   
FROM TB_BS_USR 
WHERE  
   1=1
   AND 
      (
	  RESET = 'N' 
	      OR (
		      RESET = 'Y' 
		      AND 
		      MOD_DATE <= #{expiredDateTime,jdbcType=TIMESTAMP}
	      )
	  )
```
  
### 2️⃣ Querydsl로 변환
  
```java
queryFactory.selectFrom(qUser)  
    .where(new BooleanBuilder()
        .andAnyOf(
            qUser.reset.eq("N").orAllOf(
                qUser.reset.eq("Y"), 
                qUser.modDate.loe(expireDatetime)
            )
        )
    ).fetch();
```
  
## 장점과 단점
  
### ✅ 장점
- SQL의 복잡한 논리 조건을 직관적인 코드로 변환 가능  
- 조건을 동적으로 추가할 수 있어 코드 재사용성이 높음  
  
### ❌ 단점
- 구조가 복잡해질 경우 가독성이 떨어질 수 있음  
- Querydsl 전용 기능이므로 JPA 표준이 아님  

---
  
# 연결문서
- [BooleanExpression](../../jpa/jpa-BooleanExpression)
- [Querydsl](../../jpa/jpa-Querydsl)
