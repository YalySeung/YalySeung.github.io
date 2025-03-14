---
title : "Querydsl DynamicQuery"
excerpt : "Querydsl DynamicQuery"
toc : true
toc_sticky : true
toc_label : "Querydsl DynamicQuery"
categories:
- JPA
tags:
- [Spring, JPA, Querydsl]
last_modified_at: 2024-05-10T08:00:00-10:00:00
---
  
---
  
## 특정 조건에 따라 limit, offset을 적용해야 할 경우
  **JPAQuery** 를 사용하여 limit, offset을 적용하기 전 쿼리를 선언하고, 원하는 조건에 따라 limit, offset을 적용한다.
  
```java
JPAQuery<RobotList> query = queryFactory.select(qRobot)  
        .from(qRobot)  
        .leftJoin(qWork)  
        .on(qRobot.lastExecuteWorkSequence.eq(qWork.workSequence))  
        .where(getWhereClause(robotSearchForm))  
        .orderBy(getOrderSpecifier(robotSearchForm.getSortKey(), robotSearchForm.getSortOrder()));  

if (robotSearchForm.getPageRowCount() > 0){  
        query.offset(robotSearchForm.getStartRowNo2())  
        .limit(robotSearchForm.getEndRowNo());  
}
```
  
## coalesce()
  각 DB별로 **null을 처리하는 함수**가 있기 때문에 Querydsl도 이에 대응하는 `coalesce()` 함수를 제공한다.
  
```java
qCustomer.age.coalesce(0).asNumber().sum()
```
  
  위 예제는 Customer 테이블의 나이 항목이 null일 경우 0을, 아닐 경우 나이를 합산하는 예시이다.
  
## from절의 재사용
  from절을 재사용하기 위해서는 `JPAQuery` 타입으로 쿼리 결과를 반환한다.
  
```java
private JPAQuery<?> getNewFromClauseWorkExecutionList(String summaryType){  
    JPAQuery<?> fromQuery = queryFactory  
            .from(qTaskResultView)  
            .leftJoin(qTaskProcess)  
            .on(qTaskProcess.taskQueueSequence.eq(qTaskResultView.taskQueueSequence))  
            .leftJoin(qWork)  
            .on(qTaskResultView.workSequence.eq(qWork.workSequence));  

    if (summaryType.equals("RBT")) {  
        fromQuery.innerJoin(qRobot).on(qTaskResultView.robotSequence.eq(qRobot.robotSequence));  
    }  

    return fromQuery;  
}
```
  
## groupBy 절의 재사용
  Expression Array 타입으로 반환하면 재사용이 가능하다.
  
```java
private Expression<?>[] getWorkExecutionListGroupByClause(WorkExecutionResultSearchForm workExecutionResultSearchForm) {  
    List<Expression<?>> groupbyExpression = new ArrayList<>();  
    groupbyExpression.add(qWork.workSequence);  
    groupbyExpression.add(qWork.workName);  
    groupbyExpression.add(qTaskResultView.groupSequence);  

    if (workExecutionResultSearchForm.getSummaryType().equals("RBT")) {  
        groupbyExpression.add(qTaskProcess.taskQueueSequence);  
        groupbyExpression.add(qRobot.robotSequence);  
        groupbyExpression.add(qRobot.robotName);  
        groupbyExpression.add(qTaskResultView.lastExecuteDateTime);  
        groupbyExpression.add(qTaskResultView.endDateTime == null ? qTaskResultView.lastExecuteDateTime : qTaskResultView.endDateTime);  
    }  

    return groupbyExpression.toArray(new Expression<?>[0]);  
}
```

---
  
# 연결문서
