---
title : "Oracle 환경 구성"
excerpt : "Oracle 환경 구성"
toc : true
toc_sticky : true
toc_label : "Oracle 환경 구성"
categories:
- Oracle
tags:
- [Database, Oracle, 환경]
last_modified_at: 2023-12-08T08:00:00-10:00:00
---
  
---
  
  이 글에서는 Window PC에 Oracle DB 환경을 구성해볼 예정이다.
  
## 1. Oracle 19C 버전 설치
 [Oracle Download Link](https://www.oracle.com/kr/database/technologies/oracle19c-windows-downloads.html)  링크에 접속하여 **Oracle 계정을 생성**한다. 생성이 완료되었다면 19C 버전의 **zip 파일을 다운로드** 한다.
  
![image](../../assets/images/DownloadOracle.png){:width="70%" height="70%"}  

 다운로드가 완료되었다면 적당한 위치에 압축을 해제한다.
  
![image](../../assets/images/ExtractOracleZipFile.png){:width="70%" height="70%"}  

 압축을 해제하면 폴더 경로에 Oracle 셋업 파일이 보일 것이다. 셋업 exe 파일을 실행하여 설치를 진행하자.
  
![image](../../assets/images/ExecuteOracleSetup.png){:width="70%" height="70%"}  

순서대로 설치를 진행한다.  
  
![image](../../assets/images/OracleSetup01.png)
  
![image](../../assets/images/OracleSetup02.png)  
![image](../../assets/images/OracleSetup03.png)  
![image](../../assets/images/OracleSetup04.png)
  
![image](../../assets/images/OracleSetup04_Popup.png)
  
![image](../../assets/images/OracleSetup05.png)  
![image](../../assets/images/OracleSetup06.png)
  
![image](../../assets/images/OracleSetup07.png)  
![image](../../assets/images/OracleSetup08.png)
  
## 2. SQL Developer 설치
 DB Browser로 **SQL Developer**를 사용할 것이므로 설치를 진행한다.  [Oracle Download Link](https://www.oracle.com/database/sqldeveloper/technologies/download/)  링크에서  SQL Developer를 다운로드 한다.
  
![image](../../assets/images/DownloadSQLDeveloper.png){:width="70%" height="70%"}  

 적당한 위치에 압축을 해제한다.  
  
![image](../../assets/images/ExtractSQLDeveloper.png){:width="70%" height="70%"}  
  
## SQL Developer 실행 및 DB 연결
 프로그램 설치가 모두 완료되었다. 이제부터는 SQL Developer를 사용하여 로컬 PC에 설치된 DB에 연결을 해보자. 일단 **SQL Developer를 실행**한 후 좌측 상단 **DB 생성 버튼을 클릭**한다.
  
![image](../../assets/images/SQLDeveloper_CreateNewDatabase.png)
 
 팝업창에서 DB 정보를 입력한 후 저장하여 연결을 시도한다.
  
![image](../../assets/images/SQLDeveloper_CreateNewDatabase_01.png){:width="70%" height="70%"}  

 오라클 설치 시, 기본으로 생성되는 테이블 목록을 확인할 수 있으며, SQL Script를 실행할 수 있다.
  
![image](../../assets/images/SQLDeveloper_Result.png){:width="70%" height="70%"}

---
  
# 연결문서
