---
title : "JPAExpressions"
excerpt : "JPAExpressions"
toc : true
toc_sticky : true
toc_label : "JPAExpressions"
categories:
- JPA
tags:
- [Spring, JPA, 미완료]
last_modified_at: 2024-04-29T08:00:00-10:00:00
---
  
---
  
## 사용법
  
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

---
  
# 연결문서
