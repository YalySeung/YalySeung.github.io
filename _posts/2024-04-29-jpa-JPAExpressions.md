---
title : "JPAExpressions"
excerpt : "JPAExpressions"
toc : true
toc_sticky : true
toc_label : "JPAExpressions"
categories:
- JPA
tags:
- [Spring, JPA]
last_modified_at: 2024-04-29T08:00:00-10:00:00
---
  
---
  
## 사용법
  
### 1️⃣ JPAExpressions를 활용한 서브쿼리 예제
  
```java
@Override  
public Integer selectCount(ProcessHistorySearchForm processHistorySearchForm) {  
    return queryFactory.select(qProcessVersion.processVersionSequence.count())  
            .from(qProcessVersion)  
            .where(  
                    qProcessVersion.processSequence.eq(JPAExpressions.select(qProcessVersion.processSequence)  
                            .from(qProcessVersion)  
                            .where(qProcessVersion.processVersionSequence.eq(processHistorySearchForm.getProcessVersionSequence()))),  
                    qProcessVersion.removeYn.eq("N"),  
                    BooleanExpressionCreator.stringEqualsIfExist(qProcessVersion.registerId, processHistorySearchForm.getRegistorId()),  
                    BooleanExpressionCreator.dateBetweenIfStartEndExist(qProcessVersion.registerDateTime, processHistorySearchForm.getStartDate(), processHistorySearchForm.getEndDate())  
            )  
            .orderBy(qProcessVersion.majorVersion.desc(), qProcessVersion.minorVersion.desc())  
            .fetchOne()  
            .intValue();  
}
```
  
## 장점과 단점
  
### ✅ 장점
- **JPA 내에서 서브쿼리를 활용하여 복잡한 쿼리 작성 가능**  
- **Querydsl과 결합하여 가독성 높은 코드 유지**  
  
### ❌ 단점
- **일부 데이터베이스에서 서브쿼리 성능 저하 가능**  
- **JPA 표준이 아니라 Querydsl 환경에서만 활용 가능**  

---
  
# 연결문서
