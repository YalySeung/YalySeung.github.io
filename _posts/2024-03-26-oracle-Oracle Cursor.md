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
  
---
  
> **Cursor란?**  
>
> 특정 sql 문장을 처리한 결과를 담는 메모리 공간을 의미한다. 
{: .notice--info}  

> **Fetch란?**  
>
> 커서에서 원하는 결과값을 추출하는 행위를 뜻한다. 
{: .notice--info}  
  
## Oracle Cursor의 종류

| Cursor 종류  | 기능                                                    |
| ---------- | ----------------------------------------------------- |
| 명시적 Cursor | 사용자가 선언해서 생성 후 사용하는 sql Cursor. 주로 여러개의 행을 처리할때 사용한다. |
| 묵시적 커서     | Oracle에서 자용으로 선언해주는 Cursor로 사용자는 생성유무를 알 수 없다.        |
  
## Oracle Cursor의 사용
1. Cursor를 선언한다.
2. Cursor 오픈한다.
3. Cursor 에서 테이블을 추출한다.
4. Cursor 종료한다.
  
## Cursor 개수 확인 방법
 sql **쿼리당 Cursor 개수**가 몇 개나 되는지 확인해보자.
  
```sql
SELECT SQL_TEXT, COUNT(SID) CNT  
FROM V$OPEN_CURSOR  
GROUP BY SQL_TEXT  
ORDER BY CNT DESC;
```

 Oracle **프로세스당 Cursor 개수**가 몇 개나 되는지 확인해보자.
  
```sql
SELECT SID, COUNT(SID) cursorcount  
FROM V$OPEN_CURSOR  
WHERE USER_NAME = 'MY_USER'  
GROUP BY SID  
ORDER BY cursorcount DESC;
```

> **caution**
>
> 여러 쓰레드에서 동시에 많은 쿼리를 실행하고 결과를 처리해야 하는 경우, 커서의 한계로 인한 문제가 발생할 수 있다. 
{: .notice--info}  

 아래 메시지는 커서 개수 부족으로 인해 발생하는 에러 메시지이다. 대부분은 **sql 쿼리를 최적화 하여 해결**할 수 있는 문제이다.

```
//에러메시지
Cause: java.sql.SQLException: ORA-01000: 최대 열기 커서 수를 초과했습니다
```

---
  
# 연결문서