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
  
---
  
 이 글에서는 **MariaDB**의 사용방법에 대해서 알아보도록 하겠다. 

 MariaDB를 설치 후, **외부에서 접속**하려면 별도 설정이 필요하다. 
  
```sql
SELECT Host,User,plugin,authentication_string FROM mysql.user;  

GRANT ALL PRIVILEGES ON *.* TO '아이디'@'111.222.%' IDENTIFIED BY '패스워드';
GRANT ALL PRIVILEGES ON *.* TO '아이디'@'접속ip' IDENTIFIED BY '패스워드';
```

 외부에서 접속할 수 있는 설정을 완료했다면, 자주 사용하는 **시간 데이터타입**에 대해 알아보자.

| 타입명       | 기능                               | 형식                           |
| --------- | -------------------------------- | ---------------------------- |
| TIME      | 시간 표기                            | HH:MM:SS                     |
| DATE      | 날짜 표기                            | YYYY-MM-DD                   |
| DATETIME  | 날짜와 시간 표기                        | YYYY-MM-DD HH:MM:SS          |
| TIMESTAMP | 날짜와 시간 표기, DATETIME보다 정밀한 시간을 표기 | YYYY-MM-DD HH:MM:SS(.FFFFFF) |

 이중에서 DATETIME과 TIMESTAMP 중 어떤 타입을 사용해야 할 지 상황에 따라 다르다. 

|     | DATETIME   | TIMESTAMP             |
| --- | ---------- | --------------------- |
| 타입  | 문자형        | 숫자형                   |
| 용량  | 8Byte      | 4Byte                 |
| 입력  | 명식적 insert | Default Insert (AUTO) |

 다음으로 사용자 관련 Query를 알아보자
 아래 쿼리는 현재 **유저 명**과 **IP 정보**를 가져온다.
  
```sql
SELECT User, Host FROM mysql.user
```

 아래 쿼리는 **사용자를 생성**한다.
  
```sql
CREATE USER <id>@<ip> IDENTIFIED BY <비밀번호> 
{: .notice}  
```

---
  
# 연결문서
- [CommonDB](../../database/database-CommonDB)