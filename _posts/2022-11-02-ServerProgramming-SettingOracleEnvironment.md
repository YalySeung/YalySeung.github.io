---
title: "Setting Oracle"
excerpt: "오라클 환경 셋팅"

categories:
- ServerProgramming

tags:
- [ServerProgramming]

toc: true
toc_sticky: true
toc_label: "Setting Oracle"

last_modified_at: 2022-11-02T08:00:00-10:00:00
---
# 오라클 19C 버전 설치
  - 오라클 계정 생성 후 다운로드를 진행한다.  
  [Oracle Download Link](https://www.oracle.com/kr/database/technologies/oracle19c-windows-downloads.html)  
  ![image](/assets/images/ServerProgramming/DownloadOracle.png){:width="70%" height="70%"}  
  - 적당한 위치에 압축을 해제한다.  
  ![image](/assets/images/ServerProgramming/ExtractOracleZipFile.png){:width="70%" height="70%"}  
  - 오라클 셋업 exe를 실행한다.  
  ![image](/assets/images/ServerProgramming/ExecuteOracleSetup.png){:width="70%" height="70%"}  
  - 순서대로 설치를 진행한다.  
  ![image](/assets/images/ServerProgramming/OracleSetup01.png){:width="70%" height="70%"}  
  ![image](/assets/images/ServerProgramming/OracleSetup02.png){:width="70%" height="70%"}  
  ![image](/assets/images/ServerProgramming/OracleSetup03.png){:width="70%" height="70%"}  
  ![image](/assets/images/ServerProgramming/OracleSetup04.png){:width="70%" height="70%"}  
  ![image](/assets/images/ServerProgramming/OracleSetup04_Popup.png){:width="70%" height="70%"}  
  ![image](/assets/images/ServerProgramming/OracleSetup05.png){:width="70%" height="70%"}  
  ![image](/assets/images/ServerProgramming/OracleSetup06.png){:width="70%" height="70%"}  
  ![image](/assets/images/ServerProgramming/OracleSetup07.png){:width="70%" height="70%"}  
  ![image](/assets/images/ServerProgramming/OracleSetup08.png){:width="70%" height="70%"}  

---

# SQL Developer 설치
  - SQL Developer 다운로드를 진행한다.  
  [Oracle Download Link](https://www.oracle.com/database/sqldeveloper/technologies/download/)  
  ![image](/assets/images/ServerProgramming/DownloadSQLDeveloper.png){:width="70%" height="70%"}  
  - 적당한 위치에 압축을 해제한다.  
  ![image](/assets/images/ServerProgramming/ExtractSQLDeveloper.png){:width="70%" height="70%"}  

---

# SQL Developer 실행 및 DB 연결
  - 좌측 상단 DB 생성 버튼 클릭  
  ![image](/assets/images/ServerProgramming/SQLDeveloper_CreateNewDatabase.png)  
  - DB 정보 입력 후 저장 및 연결  
  ![image](/assets/images/ServerProgramming/SQLDeveloper_CreateNewDatabase_01.png){:width="70%" height="70%"}  
  - 오라클 설치시, 기본으로 생성된 테이블들을 확인 할 수 있으며, SQL 쿼리문 실행이 가능한 환경 구성을 완료했다.  
  ![image](/assets/images/ServerProgramming/SQLDeveloper_Result.png){:width="70%" height="70%"}  



