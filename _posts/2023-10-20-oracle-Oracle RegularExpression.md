---
title : "Oracle RegularExpression"
excerpt : "Oracle RegularExpression"
toc : true
toc_sticky : true
toc_label : "Oracle RegularExpression"
categories:
- Oracle
tags:
- [Oracle, Database]
last_modified_at: 2023-10-20T08:00:00-10:00:00
---
  
---
  
 이 글에서는 Oracle에서 사용 가능한 정규식에 대해 알아보겠다. 
 
  Oracle 정규식은 **10g 버전 이상에서만 지원**하므로 필자는 19C 버전을 기준으로 내용을 작성하였다.

 먼저 Like 연산과 유사한 정규식 패턴 검색 함수인 **REGEXP_LIKE(\<컬럼명\>, \<정규식\>, \<정규식옵션\>)** 의 사용법이다.
  
```sql
SELECT *  
FROM TB_BZ_RBT  
WHERE REGEXP_LIKE(RBT_NM, '로봇|SH', 'i');
```
  
![image](../../assets/images/REGEXP_LIKE_Result.png)

 **REGEXP_REPLACE(<컬럼명>, <정규식>, <대체문자열>, <검색 시작위치>, <일치횟수>, <정규식옵션>)**은 정규식 패턴을 검색하여 대체 문자열로 변경한다.
  
```sql
SELECT REGEXP_REPLACE(RBT_NM, '로봇|SH', '나는대체된문자열이다', 1, 0, 'i')  
FROM TB_BZ_RBT;
```
  
![image](../../assets/images/REGEXP_REPLACE_Result.png)

 **REGEXP_INSTR(<컬럼명>, <정규식>, <시작위치>, <일치횟수>, <매칭되는 문자의 문자열 상 index>, <정규식 옵션>)** 함수는 정규식 패턴을 검색하여 해당 문자의 위치를 반환한다.
  
```sql
SELECT REGEXP_INSTR(RBT_NM, '로봇|SH', 1, 1, 0, 'i')  
FROM TB_BZ_RBT;
```
  
![image](../../assets/images/Robot_Source.png)  
![image](../../assets/images/REGEXP_INSTR_Result.png)

 **REGEXP_SUBSTR(<컬럼명>, <정규식>, <시작위치>, <일치횟수>, <정규식 옵션>)** 함수는 정규식 패턴을 검색하여 부분 문자를 추출한다.
  
```sql
SELECT REGEXP_SUBSTR(RBT_NM, '다람쥐|SH', 1, 1, 'i')  
FROM TB_BZ_RBT;
```
  
![image](../../assets/images/Robot_Source.png)  
![image](../../assets/images/REGEXP_SUBSTR_Result.png)

 **REGEXP_COUNT(<컬럼명>, <정규식>, <시작위치>, <정규식 옵션>)** 함수는 정규식 패턴을 검색하여 발견된 횟수를 반환한다. v11g 버전부터 사용 가능하다.
  
```sql
SELECT REGEXP_COUNT(RBT_NM, '다람쥐|SH', 1, 'i')  
FROM TB_BZ_RBT;
```
  
![image](../../assets/images/Robot_Source.png)  
![image](../../assets/images/REGEXP_COUNT_Result.png)

> **메타문자란?**  
>
> 검색 알고리즘을 지정하는 연산자를 의미한다. 
{: .notice--info}  
 
 **메타문자**의 종류와 기능은 아래와 같다.

| 메타문자        | 설명                                                                                                                                                                                                           |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| .           | 임의의 한 문자                                                                                                                                                                                                     |
| ?           | 앞 문자가                                                                                                                                                                                                        |
| +           | 앞 문자 하나 이상 있음                                                                                                                                                                                                |
| \*          | 앞 문자가 0개 이상 있음                                                                                                                                                                                               |
| {m}         | 선행 표현식이 정확히 m번 발생                                                                                                                                                                                            |
| {m,}        | 선행 표현식이 최소 m번 이상 발생                                                                                                                                                                                          |
| {m,n}       | 선행 표현식이 최소 m번 이상, 최대 n번 이하 발생                                                                                                                                                                                |
| [...]       | 괄호 안에 있는 리스트에 있는 임의의 단일 문자와 일치                                                                                                                                                                               |
| ^           | 문자열 시작부분과 일치                                                                                                                                                                                                 |
| $           | 문자열의 끝 부분과 일치                                                                                                                                                                                                |
| \\          | 표현식에서 후속 문자를 리터럴로 처리                                                                                                                                                                                         |
| \n          | 괄호 안에 그룹화 된 n번째 선행 하위식과 일치                                                                                                                                                                                   |
| \d          | 숫자                                                                                                                                                                                                           |
| [:class:]   | 지정된 posix 문자 클래스에 속한 임의의 문자와 일치<br>[:alpha:] 알파벳<br>[:digit:] 숫자<br>[:lower:] 알파벳 소문자<br>[:uppper:] 알파벳 대문자<br>[:alnum:] 알파벳 숫자<br>[:space:] 공백문자<br>[:punct:] 특수문자<br>[:cntrl:] 컨트롤문자<br>[:print:] 출력 가능 문자 |
| [\^:class:] | 괄호안의 리스트에 없는 임의의 단일문자와 일치                                                                                                                                                                                    |

> **리터럴문자란?**  
>
> 특수한 의미 없이 그대로 해석되는 문자를 의미한다. 
{: .notice--info}  

---
  
# 연결문서
- [Regular Expression](../../expression/expression-Regular-Expression)