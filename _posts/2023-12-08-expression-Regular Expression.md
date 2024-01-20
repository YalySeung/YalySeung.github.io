---
title : "Regular Expression"
excerpt : "Regular Expression"
toc : true
toc_sticky : true
toc_label : "Regular Expression"
categories:
- Expression
tags:
- [프로그래밍언어, Expression]
last_modified_at: 2023-12-08T08:00:00-10:00:00
---

# 날짜 : 2023-12-08 15:49

# 태그 : #프로그래밍언어 #Expression 
---

# 내용

## 정의
> **정규식이란?**
>
> 문자열 집합을 표현하는 형식 언어
{: .notice--info}

## 참고 사이트
- <https://regexr.com/5mhou> : 정규식 테스트 웹페이지

## Regex 사용법

### 기본 형태
- /[검색할 식]/[검색옵션(flag)]  
  

### 검색옵션(flag)
- g : global -> 문자열에서 패턴 매칭이 반복되는 문자를 전체에서 검색
- i : case insensitive -> 대소문자 구분
- m : multiline -> 한줄을 한 문장으로 인식
- s : single line -> 텍스트 전체를 한 문장으로 인식
- u : unicode -> 유니코드 문자룰로 검색
- y : sticky -> 문자 내 특정 위치에서 검색

### 그룹과 범위
- \| : 또는
- () : 그룹
- [] : 문자집합
- [^] : 부정 문자집합
- ?: : 찾지만 기억하지 않음  

[그룹과-범위-실습](#그룹과-범위-실습)

### 수량자(Quantifiers)
- ? : 0 <= [문자] <= 1
- \* : 0 <= [문자]
- \+ : 1 <= [문자]
- {n} : n번 반복
- {min,} : n번 이상
- {min,max} : min 이상 max 이하

[수량자-실습](#수량자-실습)

### 경계범위(Boundary-type)
- \b : 단어 경계
- \B : 단어 경계 아님
- ^ : 문장의 시작
- $ : 문장의 끝

[경계범위-실습](#경계범위-실습)

### 문자 클래스
- \\ : 특수문자가 아닌 문자
- . : 줄바꿈 문자를 제외한 모든 문자
- \d : digit 숫자
- \D : digit 숫자 아닌 문자
- \w : word 문자
- \W : word 문자가 아닌 문자
- \s : 공백
- \S : 공백 아닌 문자

[문자-클래스-실습](#문자-클래스-실습)

## 실습

### 그룹과 범위 실습

#### \| : 또는  
  
![image](../../assets/images/or1.png)  
![image](../../assets/images/or2.png)

#### () : 그룹
  
![image](../../assets/images/group1.png)
  
![image](../../assets/images/group2.png)

#### [] : 문자집합  
  
![image](../../assets/images/brakets1.png)
  
![image](../../assets/images/brakets2.png)

#### ?: : 찾지만 기억하지 않음  
  
![image](../../assets/images/forget.png)  

#### \[^\] : 문자집합의 여집합  
  
![image](../../assets/images/not_brakets.png)

### 수량자 실습

#### ? : 0 <= [문자] <= 1  
  
![image](../../assets/images/qeustionMark.png)

#### \* : 0 <= [문자]  
  
![image](../../assets/images/multiply.png)

#### \+ : 1 <= [문자]  
  
![image](../../assets/images/plus.png)

#### {n} : n번 반복  
  
![image](../../assets/images/repeatNumber.png)

#### {min,} : n번 이상  
  
![image](../../assets/images/repeatMin%201.png)

#### {min,max} : min 이상 max 이하  
  
![image](../../assets/images/repeatMinMax.png)  

### 경계범위 실습

#### \b : 단어 경계  
  
![image](../../assets/images/b1.png)
  
![image](../../assets/images/b2.png)

#### \B : 단어 경계 아님  
  
![image](../../assets/images/bigB1.png)
  
![image](../../assets/images/bigB2.png)

#### ^ : 문장의 시작  
  
![image](../../assets/images/angle1.png)
  
![image](../../assets/images/angle2.png)

#### $ : 문장의 끝  
  
![image](../../assets/images/dolar.png)

### 문자 클래스 실습

#### \\ : 특수문자 prefix  
  
![image](../../assets/images/backSlash.png)

#### . : 줄바꿈 문자를 제외한 모든 문자  
  
![image](../../assets/images/dot.png)

#### \\d : digit 숫자  
  
![image](../../assets/images/digit.png)

#### \\D : digit 숫자 아닌 문자  
  
![image](../../assets/images/not_digit.png)

#### \\w : word 문자  
  
![image](../../assets/images/word.png)

#### \\W : word 문자가 아닌 문자  
  
![image](../../assets/images/not_word.png)

#### \\s : 공백  
  
![image](../../assets/images/space.png)

#### \\S : 공백 아닌 문자  
  
![image](../../assets/images/not_space.png)  

### 웹페이지에서 실습
- 페이지 주소에서 도메인만 가져오기!  
  
![image](../../assets/images/match.png)
- match 함수 결과 배열의 첫번째 인덱스에 정규식과 일치하는 문자열을 확인 할 수 있다.

---

# 연결문서
