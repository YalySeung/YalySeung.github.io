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

# 날짜 : 2023-10-11 15:30

# 태그 : #Database #Oracle
---

# 내용

## 함수

### TO_DATE
- TO_DATE(<날짜문자열>, <날짜포멧>) 
- string 타입의 값을 날짜 형식으로 변환

```sql
TO_DATE('20230101', 'YYYYMMDD') -- 날짜형식 변환
TO_DATE('20230101', 'YYYYMMDD') + 1 -- 다음날짜
TO_DATE('20200324173021', 'YYYYMMDDHH24MISS') -- 시분초
```

### NVL
- NVL(\<값\>, \<지정값\>)
- \<값\>이 NULL 인 경우 지정값을 출력, 아니면 원본값 출력

```sql
NVL(name, 0)
```

### NVL2
- NVL(\<값\>, \<지정값1\>, \<지정값2\>)
- \<값\>이 NULL 이 아닌 경우 지정값1을 출력, NULL 이면 지정값2 출력

```sql
NVL2(comm, 'Y', 'N')
```

### REPLACE
- REPLACE(<컬럼명>,  <변경대상 문자열>, <변경결과 문자열>)

```SQL
UPDATE mytable SET FILE_PATH = REPLACE(FILE_PATH, '\\', '\/')
```

- ---

# 연결문서
- [CommonDB](../../database/database-CommonDB)
- [Oracle 환경 구성](../../oracle/oracle-Oracle-환경-구성)
