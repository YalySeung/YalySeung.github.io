---
title: "SQL Developer With Oracle"
excerpt: "Oracle SQL Devleoper 사용"

categories:
- ServerProgramming

tags:
- [ServerProgramming]

toc: true
toc_sticky: true
toc_label: "SQL Developer With Oracle"

last_modified_at: 2022-11-05T08:00:00-10:00:00
---

# Oracle 데이터 구조
## 물리적 구조
  - 데이터 파일 및 폴더 구조
  - *.dbf, *.ora 등의 파일

## 논리적 구조
  - OS에서는 식별할 수 없는 오라클 내부 구조
  ![image](/assets/images/ServerProgramming/OracleStructure.png)

### TableSpace
  - Segment들을 분리하여 보관하는 논리적 단위
  - 한개 이상의 데이터 파일로 구성
  - TableSpace 가 모여 DataBase를 구성한다.

### Segment
  - Extent들의 집합을 의미하는 논리적 단위
  - Table, Index, Undo, Temp

### Extent
  - Data Block들의 집합을 의미하는 논리적 단위
  - 테이블별로 구역을 나눠, 검색 범위를 줄이기위해 사용
  - 새로운 Extent를 할당받을때 기본적으로 8개의 블록(64KB)를 할당 받는다.

### Data Block
  - 가장 작은 논리적 데이터 단위
  - 한 블록당 8KB의 공간을 할당

---

# 테이블 스페이스 생성
  - DBA 윈도우를 띄운다.  

  ![image](/assets/images/ServerProgramming/SQLDeveloper_CreateTableSpace_01.png){: width="30%" height="30%"}  

  ![image](/assets/images/ServerProgramming/SQLDeveloper_CreateTableSpace_02.png){: width="40%" height="40%"}  

  - 파일 사양 탭에서 필요한 정보들을 입력한다. 이름 항목에는 <span style="color:red">.DBF 확장자를 꼭 붙여주자</span>  

  ![image](/assets/images/ServerProgramming/SQLDeveloper_CreateTableSpace_03.png){: width="70%" height="70%"}  


# 유저 생성
  ![image](/assets/images/ServerProgramming/SQLDeveloper_CreateUser_01.png){: width="30%" height="30%"}  

  - 사용자 탭에서 접근할 Table Space를 선택한다.  

  ![image](/assets/images/ServerProgramming/SQLDeveloper_CreateUser_02.png){: width="70%" height="70%"}  

  - 롤과 할당량을 설정한 후 적용버튼을 선택한다.  

  ![image](/assets/images/ServerProgramming/SQLDeveloper_CreateUser_03.png){: width="40%" height="40%"}  
  
  ![image](/assets/images/ServerProgramming/SQLDeveloper_CreateUser_04.png){: width="70%" height="70%"}  


# DB 연결
  - 계정 정보를 입력하면 접속 완료!  

  ![image](/assets/images/ServerProgramming/SQLDeveloper_ConnectTableSpace.png){: width="70%" height="70%"}  

  ![image](/assets/images/ServerProgramming/SQLDeveloper_ConnectTableSpace_Result.png){: width="50%" height="50%"}  

