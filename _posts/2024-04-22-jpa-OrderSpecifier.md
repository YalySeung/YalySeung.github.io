---
title : "OrderSpecifier"
excerpt : "OrderSpecifier"
toc : true
toc_sticky : true
toc_label : "OrderSpecifier"
categories:
- JPA
tags:
- [Spring, JPA, 미완료]
last_modified_at: 2024-04-22T08:00:00-10:00:00
---
  
---
  
## 역할
[Querydsl](../../jpa/jpa-Querydsl)에서 orderBy 절을 동적으로 처리하기 위한 Class로, **동적으로 조건절 추가** 및 **다중 조건 설정**이 필요할 경우 사용한다.
  
## Eample
  
### 선언
  
#### 조건 1가지
  
```java
private OrderSpecifier getOrderSpecifier(String sortKey, String sortOrder) {  
  
    Order order = sortOrder != null && !sortOrder.isEmpty() ? Order.valueOf(sortOrder) : Order.ASC;  
  
    if (sortKey != null && !sortKey.isEmpty())  
        switch (sortKey) {  
            case "sortHolidayDate":  
                return new OrderSpecifier(order, qHoliday.holidayDate);  
            case "sortHolidayName":  
                return new OrderSpecifier(order, qHoliday.holidayName);  
            case "sortHolidayTypeCd":  
                return new OrderSpecifier(order, qHoliday.holidayTypeCode);  
        }  
  
    return new OrderSpecifier(order, qHoliday.holidayDate);  
}
```
  
#### 조건 2가지 이상
정렬 조건이 2가지 이상일 경우, **OrderSpecifier[]**를 반환하는 함수를 추가하여 orderby 절에 Parameter로 사용한다.
  
```java
private OrderSpecifier[] getOrderSpecifier(String sortKey, String sortOrder) {  
    List<OrderSpecifier> orderSpecifiers = new ArrayList<>();  
  
    if (StringUtils.hasText(sortKey)){  
        if (sortKey.equals("version")){  
            orderSpecifiers.add(new OrderSpecifier(Order.valueOf(sortOrder), qProcessVersion.majorVersion));  
            orderSpecifiers.add(new OrderSpecifier(Order.valueOf(sortOrder), qProcessVersion.minorVersion));  
        } else if (sortKey.equals("registerDateTime")) {  
            orderSpecifiers.add(new OrderSpecifier(Order.valueOf(sortOrder), qProcessVersion.registerDateTime));  
        }  
        else {  
            orderSpecifiers.add(new OrderSpecifier(Order.DESC, qProcessVersion.majorVersion));  
            orderSpecifiers.add(new OrderSpecifier(Order.DESC, qProcessVersion.minorVersion));  
        }  
    }  
    else{  
        orderSpecifiers.add(new OrderSpecifier(Order.DESC, qProcessVersion.majorVersion));  
        orderSpecifiers.add(new OrderSpecifier(Order.DESC, qProcessVersion.minorVersion));  
    }  
  
    return orderSpecifiers.toArray(new OrderSpecifier[orderSpecifiers.size()]);  
}
```
  
#### Case 문 포함
**OrderSpecifier 타입의 변수에 먼저 할당** 후 orderSpecifiers에 Add해야 한다.
  
```java
OrderSpecifier<Integer> orderSpecifier = new CaseBuilder()  
        .when(qRobot.robotStatusCode.eq("CNCT")).then(1)  
        .when(qRobot.robotStatusCode.eq("REG")).then(2)  
        .when(qRobot.robotStatusCode.eq("DSCN_RBT")).then(3)  
        .when(qRobot.robotStatusCode.eq("DSCN_SVR")).then(4)  
        .when(qRobot.robotStatusCode.eq("WRKG")).then(5)  
        .when(qRobot.robotStatusCode.eq("RSRTG")).then(6)  
        .when(qRobot.robotStatusCode.eq("STOP")).then(7)  
        .otherwise(8)  
        .asc();  
orderSpecifiers.add(orderSpecifier);
```
  
### 사용
  
```java
@Override  
public List<HolidayCodeName> selectHolidayList(HolidaySearchForm holidaySearchForm) {  
    return queryFactory.selectfrom(qHoliday)
            .where(qHoliday.holidayDate.between(holidaySearchForm.getStartDate(), holidaySearchForm.getEndDate()))  
            .orderBy(getOrderSpecifier(holidaySearchForm.getSortKey(), holidaySearchForm.getSortOrder()))  
            .offset(holidaySearchForm.getStartRowNo2())  
            .limit(holidaySearchForm.getPageRowCount())  
            .fetch();  
}
```
  
---
  
# 연결문서
- [Querydsl](../../jpa/jpa-Querydsl)