---
title : "Expressions"
excerpt : "Expressions"
toc : true
toc_sticky : true
toc_label : "Expressions"
categories:
- JPA
tags:
- [Spring, JPA, Querydsl]
last_modified_at: 2024-05-11T08:00:00-10:00:00
---
  
---
  
> **Expressions란?**  
>
>  Querydsl 환경에서 Expression을 생성해주는 Factory Class이다. 
{: .notice--info}  

  `Expressions`를 사용하면 **Querydsl에서 동적으로 SQL 표현식을 생성하고 조작할 수 있다.**
  
## 주요 기능
  
| functionName   | 기능       |
| -------------- | -------- |
| nullExpression | null값 반환 |
  
![image](../../assets/images/ExpressionsStructure.png)
  
## 사용법
  
### 1️⃣ `Expressions`을 활용한 예제
  
```java
import com.querydsl.core.types.dsl.Expressions;
import com.querydsl.core.types.dsl.StringExpression;

StringExpression expr = Expressions.stringTemplate("FUNCTION('UPPER', {0})", "test");
```
  
## 장점과 단점
  
### ✅ 장점
- **Querydsl에서 동적 SQL 표현식을 쉽게 생성 가능**  
- **기존 DSL 표현식과 결합하여 활용 가능**  
  
### ❌ 단점
- **사용법이 다소 복잡할 수 있음**  
- **JPA 표준이 아니므로 Querydsl 환경에서만 동작**  

---
  
# 연결문서
