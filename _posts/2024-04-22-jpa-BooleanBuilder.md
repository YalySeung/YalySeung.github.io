---
title : "BooleanBuilder"
excerpt : "BooleanBuilder"
toc : true
toc_sticky : true
toc_label : "BooleanBuilder"
categories:
- JPA
tags:
- [미완료, Spring, JPA, Querydsl]
last_modified_at: 2024-04-22T08:00:00-10:00:00
---
  
---
  
 BooleanBuilder 는 QueryDSL에서 제공하는 class 중 하나로, 동적으로 조건을 구성하고 조합할 수 있는 기능을 제공한다.
  
## 주요 메서드
  
| 메서드 명    | 기능                                   |
| -------- | ------------------------------------ |
| and      | AND 조건으로 조합한다.                       |
| or       | OR 조건으로 조합한다.                        |
| not      | 부정을 추가한다.                            |
| andAnyOf | AND ( A OR B )                       |
| orAllof  | OR ( A AND B )                       |
| build    | 내부 조건을 조합하여 BooleanExpression을 반환한다. |

 BooleanBuilder의 특징은 build 반환값이 BooleanExpression이라는 것이다. 
  
## andAnyOf(), orAllOf()
 Querydsl은 or 조건보다 and의 우선순위가 높고, Java소스에서 괄호로 묶는다고 해도 우선순위가 변하지 않는다. Querydsl을 사용하다보면 and(A or B) 와 같은 조건이 필요할 경우가 있는데 이때, **andAnyOf** 를 사용한다
 간단한 예시를 들어보자
  
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
 
 복잡한 조건식이 들어있는 이 예시의 형태를 간단히 보면 **A and (B or (C and D))**의 구조이다. querydsl로 변환해보면
  
```java
queryFactory.selectFrom(qUser)  
        .where(  new BooleanBuilder().andAnyOf(qUser.reset.eq("N").orAllOf(qUser.reset.eq("Y"), qUser.modDate.loe(expireDatetime)))
        .fetch();
```

 이렇게 변환할 수 있다.

---
  
# 연결문서
- [BooleanExpression](../../jpa/jpa-BooleanExpression)
- [Querydsl](../../jpa/jpa-Querydsl)