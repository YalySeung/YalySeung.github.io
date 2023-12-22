---
title : "Oracle 환경 구성"
excerpt : "Oracle 환경 구성"
toc : true
toc_sticky : true
toc_label : "Oracle 환경 구성"
categories:
- Oracle
tags:
- [Database, Oracle, 환경구성]
last_modified_at: 2023-12-08T08:00:00-10:00:00
---

# 날짜 : 2023-12-08 12:21

# 태그 : #Database #Oracle #환경구성 
---

# 내용

## 오라클 19C 버전 설치
- 오라클 계정 생성 후 다운로드를 진행한다.  [Oracle Download Link](https://www.oracle.com/kr/database/technologies/oracle19c-windows-downloads.html)  
  
![image](../../assets/images/DownloadOracle.png){:width="70%" height="70%"}  

- 적당한 위치에 압축을 해제한다.  
  
![image](../../assets/images/ExtractOracleZipFile.png){:width="70%" height="70%"}  

- 오라클 셋업 exe를 실행한다.  
  
![image](../../assets/images/ExecuteOracleSetup.png){:width="70%" height="70%"}  

- 순서대로 설치를 진행한다.  
  
![image](../../assets/images/OracleSetup01.png)
  
![image](../../assets/images/OracleSetup02.png)  
![image](../../assets/images/OracleSetup03.png)  
![image](../../assets/images/OracleSetup04.png)
  
![image](../../assets/images/OracleSetup04_Popup.png)
  
![image](../../assets/images/OracleSetup05.png)  
![image](../../assets/images/OracleSetup06.png)
  
![image](../../assets/images/OracleSetup07.png)  
![image](../../assets/images/OracleSetup08.png)

## SQL Developer 설치
- SQL Developer 다운로드를 진행한다.   [Oracle Download Link](https://www.oracle.com/database/sqldeveloper/technologies/download/)  
  
![image](../../assets/images/DownloadSQLDeveloper.png){:width="70%" height="70%"}  

- 적당한 위치에 압축을 해제한다.  
  
![image](../../assets/images/ExtractSQLDeveloper.png){:width="70%" height="70%"}  

## SQL Developer 실행 및 DB 연결
- 좌측 상단 DB 생성 버튼 클릭  
   
![image](../../assets/images/SQLDeveloper_CreateNewDatabase.png)
- DB 정보 입력 후 저장 및 연결  
  
![image](../../assets/images/SQLDeveloper_CreateNewDatabase_01.png){:width="70%" height="70%"}  

- 오라클 설치시, 기본으로 생성된 테이블들을 확인 할 수 있으며, SQL 쿼리문 실행이 가능한 환경 구성을 완료했다.  
  
![image](../../assets/images/SQLDeveloper_Result.png){:width="70%" height="70%"}

---

# 연결문서
