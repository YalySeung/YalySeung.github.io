---
title : "JDBC"
excerpt : "JDBC"
toc : true
toc_sticky : true
toc_label : "JDBC"
categories:
- ServerCommon
tags:
- [ServerCommon, Database]
last_modified_at: 2024-03-12T08:00:00-10:00:00
---
  
---
  
## 정의
> **JDBC란?**  
>
> Java 프로그래밍 언어와 다양한 데이터베이스의 데이터 사이에 독립적 연결을 지원하는 표준 인터페이스 
{: .notice--info}  
  
## JDBC Standard Interface
- **모든 DBMS 및 Persistence Framework는 이 Interface들을 구현**한다.

| Interface  | 기능     |
| ---------- | ------ |
| Connection | 연결     |
| Statement  | SQL 전달 |
| ResultSet  | 결과 응답  |
  
## JDBC Flow
  
![image](../../assets/images/JDBCWorkflow.png)
1. JDBC 로딩 : DriverManager를 통한 JDBC 드라이버 로드
2. Conncection 생성 : DriverManager를 통한 Session Connection 객체 생성
3. Statement 객체 생성 : Statement는 SQL쿼리문 실행을 위한 객체로 SQL쿼리 문자열을 입력 받는다.
4. Query 실행 : 생성된 Statement 객체를 이용하여 쿼리 실행
5. ResultSet 객체로부터 데이터 조회 : 실행된 SQL 쿼리문의 결과
6. 객체 Close : 생성된 객체들을 역순으로 Close

---
  
# 연결문서
- [ORM](../../servercommon/servercommon-ORM)
- [DBCP](../../servercommon/servercommon-DBCP)
- [영속성(Persistence)](../../servercommon/servercommon-영속성(Persistence))