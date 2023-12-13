---
title : "MariaDB"
excerpt : "MariaDB"
toc : true
toc_sticky : true
toc_label : "MariaDB"
categories:
- MariaDB
tags:
- [Database, MariaDB]
last_modified_at: 2023-10-11T08:00:00-10:00:00
---

# 날짜 : 2023-10-11 16:09

# 태그 : #Database #MariaDB
---

# 내용

### 외부접속 허용 방법

```sql
SELECT Host,User,plugin,authentication_string FROM mysql.user;  

GRANT ALL PRIVILEGES ON *.* TO '아이디'@'111.222.%' IDENTIFIED BY '패스워드';
GRANT ALL PRIVILEGES ON *.* TO '아이디'@'접속ip' IDENTIFIED BY '패스워드';
```

### 함수

#### DATE_FORMAT
- DATE_FORMAT(<문자열>, <포맷>)
- 문자열을 날짜 형식으로 변환

```sql
DATE_FORMAT(P.PRCS_END_DT, '%Y%m%d')
```

#### DATE_ADD
- DATE_ADD(<문자열>, <날짜시간 간격의 값>)
- 날짜 연산

```sql
DATE_ADD(#{endDate, jdbcType=VARCHAR}, INTERVAL 1 DAY)
```

#### DATETIME()
- DATETIME()
- 현재 시각

```sql
SELECT DATETIME()
```

#### CAST

```sql
CAST(expr AS type)
```

---

# 연결문서
- [CommonDB](../../database/Database-CommonDB)