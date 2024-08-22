---
title : "MariaDB Function"
excerpt : "MariaDB Function"
toc : true
toc_sticky : true
toc_label : "MariaDB Function"
categories:
- MariaDB
tags:
- [Database, MariaDB]
last_modified_at: 2024-04-13T08:00:00-10:00:00
---
  
---
  
 이 글에서는 MariaDB 의 Function 에 대해서 알아보겠다.
  
# DB를 사용하다보면 날짜 데이터를 변환하거나 비교하는 일이 잦다. 이와 관련된 함수들에 대해서 알아보자.
 
 **먼저 문자열을 날짜 형식으로 변환**할 때 사용하는 STR_TO_DATE 함수의 예시를 확인해보겠다. 함수 원형은 **STR_TO_DATE(\<입력 데이터\>, \<입력 데이터 포맷\>)** 이며, 아래 쿼리문은 포맷팅 하여 변환하는 예시이다.
  
```sql
select STR_TO_DATE('2024-04-01 23:59:59', '%Y-%m-%d %H:%i:%s');  
select STR_TO_DATE('20240401 235959', '%Y%m%d %H%i%s');
```
  
 반대로 **날짜 형식을 String으로 변환**하여 할 경우가 있다. 함수 원형은 **DATE_FORMAT(<문자열>, <포맷>)** 이며, 예시는 아래와 같다.
  
```sql
DATE_FORMAT(REG_DT, '%Y%m%d')
```
  
 때로는 다음날, 다음달, 전날, 이전달 등의 **대상 시간과 다른 시점**과 시간 비교를 해야할 경우가 있다. **그때는 DATE_ADD(<문자열>, <날짜시간 간격의 값>)** 함수를 사용한다.
  
```sql
DATE_ADD(#{endDate, jdbcType=VARCHAR}, INTERVAL 1 DAY)
```
  
 로그인 시간, 계정 생성 시간 등은 insert하는 시점에 **현재 시간** 정보를 필요로 한다. 그때는 **DATEITME()** 함수를 사용한다.
  
```sql
SELECT DATETIME()
```
  
 이외에도 **간단한 형변환**을 할 수 있는 **CAST(\<표현식\> AS \<대상타입\>)** 함수가 있다.
  
```sql
CAST(expr AS type)
```  
---
  
# 연결문서
