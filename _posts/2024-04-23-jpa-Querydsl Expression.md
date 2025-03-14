---
title : "Querydsl Expression"
excerpt : "Querydsl Expression"
toc : true
toc_sticky : true
toc_label : "Querydsl Expression"
categories:
- JPA
tags:
- [Spring, JPA, Querydsl]
last_modified_at: 2024-04-23T08:00:00-10:00:00
---
  
---
  
## 정의
> **Expression이란?**  
>
>  Querydsl에서 `select`, `from`, `where` 절에 인자로 전달되는 표현 Class이다. 
{: .notice--info}  

  Querydsl의 Expression은 **쿼리의 조건 및 결과 값을 조작하는 다양한 표현식 타입을 제공**한다.
  
## 구조
  
![image](../../assets/images/Querydsl_Expression_Structure.png)
  
## 종류
  
| 타입                   | 기능                           |
| -------------------- | ---------------------------- |
| numberExpression     | 숫자 데이터 타입에 대한 표현식 생성         |
| stringExpression     | 문자열 데이터 타입에 대한 표현식 생성        |
| booleanExpression    | Boolean 데이터 타입에 대한 표현식 생성    |
| comparableExpression | Comparable 데이터 타입에 대한 표현식 생성 |
| dateTimeExpression   | 날짜 및 시간 데이터 타입에 대한 표현식 생성    |
| entityPath           | Entity 데이터 타입에 대한 표현식 생성     |
  
## 사용법
  
### 1️⃣ Querydsl Expression 사용 예제
  
```java
@Override  
public List<FileLink> selectExpiredFileLink() {  
    return queryFactory.selectFrom(qFileLink)  
            .where(Expressions.stringTemplate("TO_DATE({0}, 'YYYY-MM-DD HH24MISS')",  
                    Expressions.stringTemplate("CONCAT({0}, '235959')",  
                            qFileLink.useExpiryDate)).loe(DateTime.now().toString("YYYY-MM-DD HH24MISS"))  
            )  
            .fetch();  
}
```
  
## 장점과 단점
  
### ✅ 장점
- **Querydsl에서 다양한 데이터 타입을 효과적으로 표현 가능**  
- **복잡한 조건을 표현식으로 쉽게 구성 가능**  
  
### ❌ 단점
- **직관적인 SQL 문법과 차이가 있어 학습 필요**  
- **JPA 표준이 아닌 Querydsl 전용 문법**  

---
  
# 연결문서
- [Querydsl](../../jpa/jpa-Querydsl)
- [BooleanExpression](../../jpa/jpa-BooleanExpression)
