---
title: "정규식(Regular Expression)"
excerpt: "문자열 검색"

categories:
- ServerProgramming 

tags:
- [ServerProgramming]

toc: true
toc_sticky: true
toc_label:  "정규식(Regular Expression)"
last_modified_at: 2022-12-15T08:00:00-10:00:00
---

# 정규식(Regular Expression) 이란? 
  - 문자열 집합을 표현하는 형식 언어

---

# 참고 사이트
  - <https://regexr.com/5mhou> : 정규식 테스트 웹페이지

---

# Regex 사용법
## 기본 형태
  - /[검색할 식]/[검색옵션(flag)]

## 검색옵션(flag)
  - g : global -> 문자열에서 패턴 매칭이 반복되는 문자를 전체에서 검색
  - i : case insensitive -> 대소문자 구분
  - m : multiline -> 한줄을 한 문장으로 인식
  - s : single line -> 텍스트 전체를 한 문장으로 인식
  - u : unicode -> 유니코드 문자룰로 검색
  - y : sticky -> 문자 내 특정 위치에서 검색

## 그룹과 범위
  - \| : 또는
  - () : 그룹
  - [] : 문자집합
  - [^] : 부정 문자집합
  - ?: : 찾지만 기억하지 않음  

[실습하기](#그룹과-범위-실습)

## 수량자(Quantifiers)
  - ? : 0 <= [문자] <= 1
  - \* : 0 <= [문자] 
  - \+ : 1 <= [문자]
  - {n} : n번 반복
  - {min,} : n번 이상
  - {min,max} : min 이상 max 이하

[실습하기](#수량자-실습)

## 경계범위(Boundary-type)
  - \b : 단어 경계
  - \B : 단어 경계 아님
  - ^ : 문장의 시작
  - $ : 문장의 끝

[실습하기](#경계범위-실습)

## 문자 클래스
  - \ : 특수문자가 아닌 문자
  - . : 줄바꿈 문자를 제외한 모든 문자
  - \d : digit 숫자
  - \D : digit 숫자 아닌 문자
  - \w : word 문자
  - \W : word 문자가 아닌 문자
  - \s : 공백
  - \S : 공백 아닌 문자

[실습하기](#문자-클래스-실습)

---

# 실습
## 그룹과 범위 실습
  - \| : 또는  

![image](/assets/images/ServerProgramming/RegularExpression/or1.png){: width="70%" height="70%"}

![image](/assets/images/ServerProgramming/RegularExpression/or2.png){: width="70%" height="70%"} 
  
  - () : 그룹

![image](/assets/images/ServerProgramming/RegularExpression/group1.png){: width="70%" height="70%"}    

![image](/assets/images/ServerProgramming/RegularExpression/group2.png){: width="70%" height="70%"}   

  - [] : 문자집합  

![image](/assets/images/ServerProgramming/RegularExpression/brakets1.png){: width="70%" height="70%"}   

![image](/assets/images/ServerProgramming/RegularExpression/brakets2.png){: width="70%" height="70%"}   

  - ?: : 찾지만 기억하지 않음  

![image](/assets/images/ServerProgramming/RegularExpression/forget.png){: width="70%" height="70%"}   

  - [^] : 문자집합의 여집합  

![image](/assets/images/ServerProgramming/RegularExpression/not_brakets.png){: width="70%" height="70%"}   

## 수량자 실습
  - ? : 0 <= [문자] <= 1  

![image](/assets/images/ServerProgramming/RegularExpression/qeustionMark.png){: width="70%" height="70%"}   
  
  - \* : 0 <= [문자]  

![image](/assets/images/ServerProgramming/RegularExpression/multiply.png){: width="70%" height="70%"}   
  
  - \+ : 1 <= [문자]  

![image](/assets/images/ServerProgramming/RegularExpression/plus.png){: width="70%" height="70%"}   
  
  - {n} : n번 반복  

![image](/assets/images/ServerProgramming/RegularExpression/repeatNumber.png){: width="70%" height="70%"}   
  
  - {min,} : n번 이상  

![image](/assets/images/ServerProgramming/RegularExpression/repeatMin.png){: width="70%" height="70%"}   
  
  - {min,max} : min 이상 max 이하  

![image](/assets/images/ServerProgramming/RegularExpression/repeatMinMax.png){: width="70%" height="70%"}   

## 경계범위 실습
  - \b : 단어 경계  

![image](/assets/images/ServerProgramming/RegularExpression/b1.png){: width="70%" height="70%"}   

![image](/assets/images/ServerProgramming/RegularExpression/b2.png){: width="70%" height="70%"}   

  - \B : 단어 경계 아님  

![image](/assets/images/ServerProgramming/RegularExpression/bigB1.png){: width="70%" height="70%"}   

![image](/assets/images/ServerProgramming/RegularExpression/bigB2.png){: width="70%" height="70%"}   

  - ^ : 문장의 시작  

![image](/assets/images/ServerProgramming/RegularExpression/angle1.png){: width="70%" height="70%"}   

![image](/assets/images/ServerProgramming/RegularExpression/angle2.png){: width="70%" height="70%"}   

  - $ : 문장의 끝  

![image](/assets/images/ServerProgramming/RegularExpression/dolar.png){: width="70%" height="70%"}   

## 문자 클래스 실습
  - \ : 특수문자가 아닌 문자  

![image](/assets/images/ServerProgramming/RegularExpression/backSlash.png){: width="70%" height="70%"}   

  - . : 줄바꿈 문자를 제외한 모든 문자  

![image](/assets/images/ServerProgramming/RegularExpression/dot.png){: width="70%" height="70%"}   

  - \d : digit 숫자  

![image](/assets/images/ServerProgramming/RegularExpression/digit.png){: width="70%" height="70%"}   

  - \D : digit 숫자 아닌 문자  

![image](/assets/images/ServerProgramming/RegularExpression/not_digit.png){: width="70%" height="70%"}   

  - \w : word 문자  

![image](/assets/images/ServerProgramming/RegularExpression/word.png){: width="70%" height="70%"}   

  - \W : word 문자가 아닌 문자  

![image](/assets/images/ServerProgramming/RegularExpression/not_word.png){: width="70%" height="70%"}   

  - \s : 공백  

![image](/assets/images/ServerProgramming/RegularExpression/space.png){: width="70%" height="70%"}   

  - \S : 공백 아닌 문자  

![image](/assets/images/ServerProgramming/RegularExpression/not_space.png){: width="70%" height="70%"}   

## 웹페이지에서 실습
  - 페이지 주소에서 도메인만 가져오기!  

![image](/assets/images/ServerProgramming/RegularExpression/match.png)  

  - match 함수 결과 배열의 첫번째 인덱스에 정규식과 일치하는 문자열을 확인 할 수 있다.
  