---
title : "Oracle Function"
excerpt : "Oracle Function"
toc : true
toc_sticky : true
toc_label : "Oracle Function"
categories:
- Oracle
tags:
- [Database, Oracle]
last_modified_at: 2023-10-11T08:00:00-10:00:00
---
  
---
  
 이 글에서는 Oracle에서 자주 사용되는 Function에 대해서 다루도록 하겠다.
  
## NULL 값 처리 함수

 어떤 값에 대한 NULL 체크가 필요할 경우 **NVL(\<값\>, \<지정값\>)** 함수를 사용하여 NULL 값일 경우 출력 값을 지정할 수 있다.
  
```sql
NVL(name, 0)
```
  
 NULL 체크를 하는 또 다른 방법은 **NVL2(\<값\>, \<NULL이 아닐 경우 값\>, \<Null일 경우 값\>)** 함수를 하용하는 방법이다. NVL 함수와는 다르게 NULL이 아닐경우 값도 지정할 수 있다.
  
```sql
NVL2(comm, 'Y', 'N')
```
  
## 타입 변환 함수
 **String 타입의 값을 날짜 형식으로 변환**하고 싶을 때는 **TO_DATE(<날짜문자열>, <날짜포맷>)** 함수를 사용한다.
  
```sql
TO_DATE('20230101', 'YYYYMMDD') -- 날짜형식 변환
TO_DATE('20230101', 'YYYYMMDD') + 1 -- 다음날짜
TO_DATE('20200324173021', 'YYYYMMDDHH24MISS') -- 시분초
```

 **TO_NCHAR** 함수는 CHAR, VARCHAR2, CLOB, NCLOB 등의 수치형 인수를 자국어 문자 세트 형태의 문자열로 변환하는 역할을 한다.
  
## 문자열 처리 함수
 문자열의 일부를 치환할때는 **REPLACE(<컬럼명>,  <변경대상 문자열>, <변경결과 문자열>)** 함수를 사용한다.
  
```SQL
UPDATE mytable SET FILE_PATH = REPLACE(FILE_PATH, '\\', '\/')
```
  
## 조건 분기 함수
  **DECODE(\<컬럼\>, \<조건1\>, \<결과1\>, \<조건1\>, \<결과1\>, ..., \<ELSE결과\>)** 함수는 IF ELSE와 비슷한 기능을 수행하는 함수로 표준 SQL함수가 아니기 때문에 **CASE WHEN 구문 사용을 권장한다.**
  
```sql
DECODE(JOB, 'Developer', 1, 'teacher', 2, student)
```

- ---
  
# 연결문서
- [CommonDB](../../database/database-CommonDB)
- [Oracle 환경 구성](../../oracle/oracle-Oracle-환경-구성)
