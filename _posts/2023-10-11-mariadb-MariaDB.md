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

#### STR_TO_DATE
- 문자열을 날짜 형식으로 변환
- STR_TO_DATE(\<입력 데이터\>, \<입력 데이터 포맷\>)

```sql
select STR_TO_DATE('2024-04-01 23:59:59', '%Y-%m-%d %H:%i:%s');  
select STR_TO_DATE('20240401 235959', '%Y%m%d %H%i%s');
```

#### DATE_FORMAT
- 날짜를 지정된 형식의 문자열로 변환
- DATE_FORMAT(<문자열>, <포맷>)

```sql
DATE_FORMAT(REG_DT, '%Y%m%d')
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

### 시간 데이터 타입

| 타입명       | 기능                               | 형식                           |
| --------- | -------------------------------- | ---------------------------- |
| TIME      | 시간 표기                            | HH:MM:SS                     |
| DATE      | 날짜 표기                            | YYYY-MM-DD                   |
| DATETIME  | 날짜와 시간 표기                        | YYYY-MM-DD HH:MM:SS          |
| TIMESTAMP | 날짜와 시간 표기, DATETIME보다 정밀한 시간을 표기 | YYYY-MM-DD HH:MM:SS(.FFFFFF) |

#### DATETIME과 TIMESTAMP

|     | DATETIME   | TIMESTAMP             |
| --- | ---------- | --------------------- |
| 타입  | 문자형        | 숫자형                   |
| 용량  | 8Byte      | 4Byte                 |
| 입력  | 명식적 insert | Default Insert (AUTO) |

---

# 연결문서
- [CommonDB](../../database/database-CommonDB)