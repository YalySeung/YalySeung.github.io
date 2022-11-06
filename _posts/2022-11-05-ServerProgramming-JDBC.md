---
title: "JDBC"
excerpt: "Java DB 연동 API"

categories:
- ServerProgramming

tags:
- [ServerProgramming]

toc: true
toc_sticky: true
toc_label: "JDBC"

last_modified_at: 2022-11-06T08:00:00-10:00:00
---

# 정의
  - java Database Connectivity
  - java DB 연동 인터페이스

# 구조
  ![image](/assets/images/ServerProgramming/JDBC_Struct.png)  
  - JDBC 드라이버 : DBMS 클라이언트, DBMS와 통신 담당, DB마다 다름

# 주요 클래스 및 인터페이스
  - DriverMangaer = JDBC 드라이버 로드
  - Connection : DB와 연결을 위한 인터페이스
  - Statement, PreparedStatement , CallableStatement: SQL을 보내기 위한 통로
  - ResultSet : SQL의 결과 객체

# Flow
# JDBC 드라이버 로드
# Connection 객체 생성
# Statement 객체 생성
# SQL 실행
# Result 객체 생성(select일 경우)
# Result 객체 해제(select일 경우)
# Statement 객체 해제
# Connection 객체 해제

  
  수정 작업중입니다.................