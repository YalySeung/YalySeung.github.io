---
title : "MSSQL"
excerpt : "MSSQL"
toc : true
toc_sticky : true
toc_label : "MSSQL"
categories:
- MSSQL
tags:
- [Database, MSSQL]
last_modified_at: 2023-10-11T08:00:00-10:00:00
---

# 날짜 : 2023-10-11 16:09

# 태그 : #Database #MSSQL
---

# 내용

### 함수

#### CONVERT
- 데이터 타입 변환에 사용
- CONVERT(<데이터타입>, <변환할 값>, <\style>)
- style 
	- 1: MM/DD/YY 또는 DD/MM/YY 형식
	- 3: DD/MM/YY 또는 DD/MM/YYYY 형식
	- 4: DD.MM.YY 또는 DD.MM.YYYY 형식
	- 5: DD-MM-YY 또는 DD-MM-YYYY 형식
	- 10: MM-DD-YY 또는 MM-DD-YYYY 형식
	- 11: MM/DD/YY 또는 MM/DD/YYYY 형식
	- 19: YYYY.MM.DD HH:MI:SS 형식
	- 20: YYYY-MM-DD HH:MI:SS 형식
	- 21: YYYY.MM.DD HH:MI:SS 형식
	- 112: YYYYMMDD 형식
	- 120: YYYY-MM-DD HH:MI:SS 형식 (ISO 8601 형식)
	- 126: YYYY-MM-DDTHH:MI:SS 형식 (ISO 8601 형식)
	- 130: DD Month YYYY HH:MI:SS 형식 (영어 월 이름)

```sql
CONVERT(VARCHAR, P.PRCS_END_DT, 112) -- 날짜 형식으로 변경
```

#### DATEADD
- DATEADD(<시간간격>, <시간간격의 수>, <날짜 또는 시간>)
- 날짜 연산

```sql
DATEADD(day, 3, GETDATE())
```

#### CAST
- CAST(<문자열>, <변환전 타입>) AS <변환될 타입>
- 문자열 데이터 타입 변환

```sql
CAST(#{endDate, jdbcType=VARCHAR} AS DATE
```

---

# 연결문서
- [CommonDB](../../database/Database-CommonDB)
