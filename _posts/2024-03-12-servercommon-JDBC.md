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
  
## 📌 JDBC란?

> **info**
>
> JDBC(Java Database Connectivity)는 **Java 애플리케이션이 데이터베이스에 접근할 수 있도록 지원하는 표준 API(인터페이스)**이다.  
> DBMS와 무관하게 Java 코드로 SQL을 실행하고 결과를 가져올 수 있게 해준다. 
{: .notice--info}  

---
  
## ✅ JDBC 구성 요소

| Interface  | 설명 |
|------------|------|
| `DriverManager` | 드라이버 로딩 및 커넥션 생성 |
| `Connection`    | DB 연결을 위한 세션 객체 |
| `Statement`     | SQL 쿼리 실행 객체 (PreparedStatement 포함) |
| `ResultSet`     | 쿼리 결과를 저장하고 처리하는 객체 |

---
  
## ✅ JDBC 처리 흐름
  
![image](../../assets/images/JDBCWorkflow.png)
  
```java
1. 드라이버 로딩
   Class.forName("com.mysql.cj.jdbc.Driver");

2. DB 연결
   Connection conn = DriverManager.getConnection(url, user, password);

3. SQL 실행 객체 생성
   Statement stmt = conn.createStatement();

4. 쿼리 실행
   ResultSet rs = stmt.executeQuery("SELECT * FROM users");

5. 결과 처리
   while (rs.next()) {
       System.out.println(rs.getString("username"));
   }

6. 자원 해제
   rs.close(); stmt.close(); conn.close();
```

---
  
## ✅ JDBC 사용 시 주의사항

- 자원 누수 방지: 반드시 try-with-resources 또는 close() 호출
- SQL Injection 대응: PreparedStatement 사용 권장
- 성능 최적화: Statement 대신 PreparedStatement 반복 사용

---
  
## ✅ JDBC vs ORM

| 항목 | JDBC | ORM (ex: JPA, Hibernate) |
|------|------|---------------------------|
| 접근 방식 | SQL 직접 작성 | 객체 기반 추상화 |
| 학습 난이도 | 낮음 | 상대적으로 높음 |
| 유연성 | 매우 유연 | 제한 있음 |
| 유지보수성 | SQL 변경 많음 | 엔티티 중심 설계 |

---
  
## ✅ JDBC 관련 프레임워크

- Spring JDBC
- MyBatis (SQL Mapper 기반)
- JPA (ORM 기반, 내부적으로 JDBC 사용)
- Hibernate

---
  
# 연결문서
- [ORM](../../servercommon/servercommon-ORM)
- [DBCP](../../servercommon/servercommon-DBCP)
- [영속성(Persistence)](../../servercommon/servercommon-영속성(Persistence))
