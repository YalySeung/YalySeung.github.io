---
title : "Oracle Cursor"
excerpt : "Oracle Cursor"
toc : true
toc_sticky : true
toc_label : "Oracle Cursor"
categories:
- Oracle
tags:
- [Database, Oracle]
last_modified_at: 2024-03-26T08:00:00-10:00:00
---

# 날짜 : 2024-03-26 08:51

# 태그 : #Database #Oracle
---

# 내용

## 정의
> **Cursor란?**
>
> 특정 sql 문장을 처리한 결과를 담는 메모리 공간
{: .notice--info}

> **Fetch란?**
>
> 커서에서 원하는 결과값을 추출하는 행위
{: .notice--info}

## 종류

| Cursor 종류  | 기능                                                 |
| ---------- | -------------------------------------------------- |
| 명시적 Cursor | 사용자가 선언해서 생성 후 사용하는 sql Cursor. 주로 여러개의 행을 처리할때 사용 |
| 묵시적 커서     | Oracle에서 자용으로 선언해주는 Cursor. 사용자는 생성유무를 알 수 없음      |

## Work Flow
1. Cursor 선언
2. Cursor 오픈
3. Cursor 에서 테이블 추출
4. Cursor 종료

## Cursor 개수 확인

### sql 쿼리당 Cursor 수 조회

```sql
SELECT SQL_TEXT, COUNT(SID) CNT  
FROM V$OPEN_CURSOR  
GROUP BY SQL_TEXT  
ORDER BY CNT DESC;
```

### 오라클 프로세스당 Cursor 수 조회

```sql
SELECT SID, COUNT(SID) cursorcount  
FROM V$OPEN_CURSOR  
WHERE USER_NAME = 'MY_USER'  
GROUP BY SID  
ORDER BY cursorcount DESC;
```

## Error
> **caution**
>
> 여러 쓰레드에서 동시에 많은 쿼리를 실행하고 결과를 처리해야 하는 경우, 커서의 한계로 인한 문제가 발생할 수 있다.
{: .notice--danger}

```
//에러메시지
Cause: java.sql.SQLException: ORA-01000: 최대 열기 커서 수를 초과했습니다
```

---

# 연결문서