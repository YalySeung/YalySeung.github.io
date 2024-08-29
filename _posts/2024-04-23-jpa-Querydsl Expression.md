---
title : "Querydsl Expression"
excerpt : "Querydsl Expression"
toc : true
toc_sticky : true
toc_label : "Querydsl Expression"
categories:
- JPA
tags:
- [Spring, JPA, 미완료, Querydsl]
last_modified_at: 2024-04-23T08:00:00-10:00:00
---
  
---
  
## 정의
> **Expression이란?**  
>
> Querydsl 에서 select, from, where 절에 인자로 전달되는 표현 Class 
{: .notice--info}  
  
## 구조
  
![image](../../assets/images/Querydsl_Expression_Structure.png)
  
## 종류

| 타입                   | 기능                           |
| -------------------- | ---------------------------- |
| numberExpression     | 숫자 데이터 타입에 대한 표현식 생성         |
| stringExpression     | 문자열 데이터 타입에 대한 표현식 생성        |
| booleanExpression    | Boolean 테이터 타입에 대한 표현식 생성    |
| comparableExpression | Comparable 데이터 타입에 대한 표현식 생성 |
| dateTimeExpression   | 날짜 및 시간 데이터 타입에 대한 표현식 생성    |
| entityPath           | Entity 데이터 타입에 대한 표현식 생성     |
  
## 사용법
  
### Example
  
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

---
  
# 연결문서
- [Querydsl](../../jpa/jpa-Querydsl)
- [BooleanExpression](../../jpa/jpa-BooleanExpression)