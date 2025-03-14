---
title : "Oracle Common"
excerpt : "Oracle Common"
toc : true
toc_sticky : true
toc_label : "Oracle Common"
categories:
- Oracle
tags:
- [Database, Oracle]
last_modified_at: 2023-12-12T08:00:00-10:00:00
---
  
---
  
 Oracle 의 기본 데이터 타입과 자주 사용하는 쿼리를 살펴보자. 
  
## 데이터 타입
 Oracle의 기본 데이터 타입은 크게 **문자형**, **숫자형**, **날짜형**, **LOB** 이렇게 4가지로 분류할 수 있다.
  
### 📌 문자형 데이터 타입
  
| type        | 설명             | 최대길이     | 기본값   |
| ----------- | -------------- | -------- | ----- |
| CHAR(n)     | 고정길이 문자        | 2000byte | 1byte |
| VARCHAR2(n) | 가변길이 문자        | 4000byte | 1byte |
| NACHAR(n)   | 고정길이 유니코드 문자   | 2000byte | 1byte |
| NVARCHAR(n) | 가변길이 유니코드 문자   | 2000byte | 1byte |
| LONG        | 최대값이 큰 가변길이 문자 | 2Gbyte   |       |
  
### 📌 숫자형 데이터 타입
  
| type          | 설명            | 최대길이    | 값 범위                |
| ------------- | ------------- | ------- | ------------------- |
| NUMBER(P, S)  | 가변숫자          | 22byte | P(1~38), S(-84~127) |
| FLOAT(P)      | NUMBER 하위타입   | 22byte  | P(1~128)            |
| BINARY_FLOAT  | 32bit 부동소수점 수 | 4byte   |                     |
| BINARY_DOUBLE | 64bit 부동소수점 수 | 8byte   |                     |
  
### 📌 날짜형 데이터 타입
  
| type      | 설명                                             |
| --------- | --------------------------------------------- |
| DATE      | BC 4712년 1월 1일부터 9999년 12월 31일, 연월일시분초까지 입력 가능 |
| TIMESTAMP | 연월일시분초 + 밀리초까지 입력 가능                           |
  
### 📌 LOB 데이터 타입 (대용량 데이터 저장)
  
| type  | 설명                                              |
| ----- | ------------------------------------------------- |
| CLOB  | 문자형 대용량 객체 (고정길이 및 가변길이) |
| NCLOB | 유니코드를 지원하는 문자형 대용량 객체            |
| BLOB  | 이진형 대용량 객체                                |
| BFILE | 대용량 이진 파일에 대한 위치 및 이름               |

---
  
## 📌 CRUD 예제
  
### 1️⃣ 테이블 생성
  
```sql
CREATE TABLE USERS (
    ID NUMBER PRIMARY KEY,
    NAME VARCHAR2(100),
    EMAIL VARCHAR2(100),
    CREATED_AT DATE DEFAULT SYSDATE
);
```
  
### 2️⃣ 데이터 삽입 (INSERT)
  
```sql
INSERT INTO USERS (ID, NAME, EMAIL) VALUES (1, '홍길동', 'hong@example.com');
COMMIT;
```
  
### 3️⃣ 데이터 조회 (SELECT)
  
```sql
SELECT * FROM USERS WHERE NAME = '홍길동';
```
  
### 4️⃣ 데이터 수정 (UPDATE)
  
```sql
UPDATE USERS SET EMAIL = 'hong_new@example.com' WHERE ID = 1;
COMMIT;
```
  
### 5️⃣ 데이터 삭제 (DELETE)
  
```sql
DELETE FROM USERS WHERE ID = 1;
COMMIT;
```

---
  
## 📌 시퀀스 (Sequence) 사용 예제
 시퀀스를 활용하면 **자동 증가하는 ID 값을 생성할 수 있다.**
  
### 6️⃣ 시퀀스 생성
  
```sql
CREATE SEQUENCE USER_SEQ START WITH 1 INCREMENT BY 1 NOCACHE NOCYCLE;
```
  
### 7️⃣ 시퀀스를 사용한 데이터 삽입
  
```sql
INSERT INTO USERS (ID, NAME, EMAIL) VALUES (USER_SEQ.NEXTVAL, '김철수', 'kim@example.com');
```
  
### 8️⃣ 현재 시퀀스 값 확인
  
```sql
SELECT USER_SEQ.CURRVAL FROM DUAL;
```

---
  
## 📌 ROWNUM을 활용한 페이징 처리
  
### 9️⃣ 특정 개수만 조회 (예: 상위 10개 데이터)
  
```sql
SELECT * FROM USERS WHERE ROWNUM <= 10;
```
  
### 🔟 OFFSET을 포함한 페이징 처리
  
```sql
SELECT * FROM (
    SELECT A.*, ROWNUM AS RNUM FROM (
        SELECT * FROM USERS ORDER BY CREATED_AT DESC
    ) A WHERE ROWNUM <= 20
) WHERE RNUM > 10;
```
**🔹 위 쿼리는 11번째부터 20번째 데이터만 조회하는 예제**

---
  
## 📌 날짜 및 시간 관련 예제
  
### 11️⃣ 현재 날짜 및 시간 조회
  
```sql
SELECT SYSDATE FROM DUAL;
```
  
### 12️⃣ 특정 날짜 이후 데이터 조회
  
```sql
SELECT * FROM USERS WHERE CREATED_AT >= TO_DATE('2024-01-01', 'YYYY-MM-DD');
```
  
### 13️⃣ 날짜 형식 변환
  
```sql
SELECT TO_CHAR(SYSDATE, 'YYYY-MM-DD HH24:MI:SS') FROM DUAL;
```

---
  
## 📌 기타 자주 사용하는 SQL 문법
  
### 14️⃣ 테이블에 컬럼 추가
  
```sql
ALTER TABLE USERS ADD PHONE_NUMBER VARCHAR2(20);
```
  
### 15️⃣ 테이블 컬럼 삭제
  
```sql
ALTER TABLE USERS DROP COLUMN PHONE_NUMBER;
```
  
### 16️⃣ 인덱스 생성
  
```sql
CREATE INDEX IDX_USERS_EMAIL ON USERS (EMAIL);
```
  
### 17️⃣ 테이블 삭제
  
```sql
DROP TABLE USERS CASCADE CONSTRAINTS;
```

---
  
# 연결문서
