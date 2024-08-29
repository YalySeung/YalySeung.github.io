---
title : "MSSQL Function"
excerpt : "MSSQL Function"
toc : true
toc_sticky : true
toc_label : "MSSQL Function"
categories:
- MSSQL
tags:
- [Database, MSSQL]
last_modified_at: 2023-10-11T08:00:00-10:00:00
---
  
---
  
 이 글에서는 MSSQL 에서 자주 사용되는 함수들을 알아볼 것이다.

 CONVERT 함수는 데이터 타입 변환에 사용되며, 함수 원형은 **CONVERT(<데이터타입>, <변환할 값>, <\style>)**이다.  Style 값에 따라 포맷이 정해지는데, 값에 따른 포맷은 아래 표에서 확인하자.
  
```sql
CONVERT(VARCHAR, P.PRCS_END_DT, 112) -- 날짜 형식으로 변경
```

| style 값 | 결과 형식                             |
| ------- | --------------------------------- |
| 1       | MM/DD/YY 또는 DD/MM/YY              |
| 3       | DD/MM/YY 또는 DD/MM/YYYY            |
| 4       | DD.MM.YY 또는 DD.MM.YYYY            |
| 5       | DD-MM-YY 또는 DD-MM-YYYY            |
| 10      | MM-DD-YY 또는 MM-DD-YYYY            |
| 11      | MM/DD/YY 또는 MM/DD/YYYY            |
| 19      | YYYY.MM.DD HH:MI:SS               |
| 20      | YYYY-MM-DD HH:MI:SS               |
| 21      | YYYY.MM.DD HH:MI:SS               |
| 112     | YYYYMMDD                          |
| 120     | YYYY-MM-DD HH:MI:SS (ISO 8601 형식) |
| 126     | YYYY-MM-DDTHH:MI:SS (ISO 8601 형식) |
| 130     | DD Month YYYY HH:MI:SS (영어 월 이름)  |
  
 또 하나의 **타입 변환** 방법은 **CAST(<문자열>, <변환전 타입>) AS <변환될 타입>)** 함수를 사용하는 것이다.
  
```sql
CAST(#{endDate, jdbcType=VARCHAR} AS DATE
```
  
 날짜 타입 데이터에 가감을 위해서는 **DATEADD(<시간간격>, <시간간격의 수>, <날짜 또는 시간>)** 함수를 사용한다.
  
```sql
DATEADD(day, 3, GETDATE())
```
  
 MSSQL에는 **여러 행의 컬럼을 하나로 합치**는 **STUFF(<문자열>, <시작위치>, <문자길이>, <치환문자>)** 함수가 존재한다.
  
```sql
SELECT a.birthday, 
	STUFF((SELECT ',' + userId  
			FROM user  
			WHERE birthday = a.birthday
			FOR XML PATH('')), 1, 1, '') AS userIds
FROM user AS a  
GROUP BY a.birthday
```

---
  
# 연결문서
- [CommonDB](../../database/database-CommonDB)
