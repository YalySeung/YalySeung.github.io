---
title : "Oracle Common"
excerpt : "Oracle Common"
toc : true
toc_sticky : true
toc_label : "Oracle Common"
categories:
- Oracle
tags:
- [Database, Oracle, 미완료]
last_modified_at: 2023-12-12T08:00:00-10:00:00
---

# 날짜 : 2023-12-12 17:07

# 태그 : #Database #Oracle #미완료 
---

# 내용

## 데이터타입

### 문자형

| type | 설명                          | 최대길이 | 기본값 |
| ----------- | ----------------------------- | -------- | ------ |
| CHAR(n)     | 고정길이 문자                 | 2000byte | 1byte  |
| VARCHAR2(n) | 가변길이 문자                 | 4000byte | 1byte  |
| NACHAR(n)   | 고정길이 유니코드 문자        | 2000byte | 1byte  |
| NVARCHAR(n) | 가변길이 유니코드 문자        | 2000byte | 1byte  |
| LONG        | 최대값이 큰 가변길이 문자     | 2Gbyte   |        |
| CLOB        | 대용량 텍스트 데이터          | 4Gbyte   |        |
| NCLOB       | 대용량 텍스트 유니코드 데이터 | 4Gbyte   |        |

### 숫자형

| type          | 설명                | 최대길이 |   값 범위  |
| ------------- | ------------------- | -------- | --- |
| NUMBER(P, S)  | 가변숫자            | 22btype  | P(1~38), S(-84~127)    |
| FLOAT(P)      | NUMBER 하위타입     | 22byte   |  P(1~128)   |
| BINARY_FLOAT  | 32bit 부동소수점 수 | 4byte    |     |
| BINARY_DOUBLE | 64bit 부동소수점 수 | 8byte    |     |

### 날짜형

| type      | 설명                                                               |
| --------- |:------------------------------------------------------------------ |
| DATE      | BC 4712년 1월 1일부터 9999년 12월 31일, 연월일시분초까지 입력 가능 |
| TIMESTAMP | 연월일시분초 + 밀리초까지 입력 가능                                |

### LOB 데이터 타입

| type  | 설명                                              |
| ----- | ------------------------------------------------- |
| CLOB  | 문자형 대용량 객체 고정길이와 가변길이의 문자집합 |
| NCLOB | 유니코드를 지원하는 문자형 대용량 객체            |
| BLOB  | 이진형 대용량 객체                                |
| BFILE | 대용량 이진 파일에 대한 위치, 이름                |

## 테이블 수정

```sql
ALTER TABLE <테이블명>
ADD <컬럼명> <컬럼타입> DEFAULT <기본값>;
```

---

# 연결문서
