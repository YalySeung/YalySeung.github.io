---
title : "벌크연산"
excerpt : "벌크연산"
toc : true
toc_sticky : true
toc_label : "벌크연산"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-04-09T08:00:00-10:00:00
---
  
---
  
## 📌 벌크 연산(Bulk Operation)이란?

> **info**
>
> 벌크 연산은 **데이터베이스나 프로그램에서 다수의 데이터를 한 번에 처리**하는 작업을 의미한다.  
> 이는 **성능 향상**, **트랜잭션 오버헤드 감소**, **네트워크 효율성 증가** 등의 목적에서 사용된다. 
{: .notice--info}  

---
  
## ✅ 벌크 연산의 장점

- **성능 향상**: 반복적인 SQL 실행 횟수를 줄임
- **트랜잭션 처리 감소**: 커밋 횟수 줄이기 가능
- **네트워크 부하 감소**: 클라이언트 ↔ DB 간 왕복 최소화
- **코드 단순화**: 반복문 없이 집합 단위 처리

---
  
## ✅ 주의할 점

- **메모리 사용량 증가**: 대량의 데이터 로딩 시 서버 자원 소모
- **DB 락 및 부하**: 동시에 너무 많은 작업 처리 시 DB 응답성 저하
- **에러 핸들링 복잡**: 일부 실패에 대한 롤백 전략 필요

---
  
## ✅ 벌크 연산 예시 (SQL)
  
### 🔹 벌크 삽입
  
```sql
INSERT INTO employees (name, position, salary) 
VALUES 
('John Doe', 'Developer', 60000), 
('Jane Smith', 'Manager', 75000), 
('Alice Johnson', 'Analyst', 50000);
```
  
### 🔹 벌크 수정
  
```sql
UPDATE employees 
SET salary = salary * 1.10 
WHERE position = 'Developer';
```
  
### 🔹 벌크 삭제
  
```sql
DELETE FROM employees 
WHERE position = 'Intern';
```

---
  
## ✅ 벌크 연산 예시 (Java JDBC)
  
```java
String sql = "INSERT INTO log (message) VALUES (?)";
PreparedStatement pstmt = connection.prepareStatement(sql);

for (String msg : messages) {
    pstmt.setString(1, msg);
    pstmt.addBatch();
}

pstmt.executeBatch(); // 벌크 실행
```

---
  
## ✅ 벌크 연산 관련 기술

- Hibernate: `session.save()` + `flush()` + `clear()` 반복 처리
- JPA: `EntityManager.persist()` + 벌크 연산용 쿼리 (주의 필요)
- MyBatis: `<foreach>` 사용하여 XML 매핑

---
  
# 연결문서