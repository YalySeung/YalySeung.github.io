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
  
---
  
> **정규식이란?**  
>
> 문자열 집합을 표현하는 형식 언어를 뜻한다. 
{: .notice--info}  

 문자열 검색에서 많이 사용되는 정규식에 대해서 알아보겠다.

 정규식의 기본 형태는 아래와 같다.
```
<검색할 식>/<검색옵션(flag)> 
{: .notice}  
```

 먼저 검색 옵션에 대해서 알아보자. **검색 옵션**에서는 **검색 범위**와 **대소문자 구분** 그리고 **유니코드 검색** 등의 **검색 방법에 대한 설정**을 할 수 있다.

| 검색옵션 | 의미               | 기능                            |
| ---- | ---------------- | ----------------------------- |
| g    | global           | 문자열에서 패턴 매칭이 반복되는 문자를 전체에서 검색 |
| i    | case insensitive | 대소문자 구분                       |
| m    | multi line       | 한 줄을 한 문장으로 인식                |
| s    | single line      | 텍스트 전체를 한 문장으로 인식             |
| u    | unicode          | 유니코드 문자 rule로 검색              |
| y    | sticky           | 문자 내 특정 위치에서 검색               |

 다음으로 검색할 식의 syntax에 대해서 알아보자. 검색할 식은 크게 **그룹과 범위**, **수량자**, **경계범위**, **문자 클래스** 등을 지정할 수 있다. 각 항목 별 Keywork와 예제를 살펴보자. 예제에서 검색 옵션은 기본 옵션인 **/g**로 설정하였다.
  
## 그룹과 범위 지정
 문자간 **논리 연산**과 **grouping**을 설정하는 Keyword의 모음이다.

| Keyword | 기능           |
| ------- | ------------ |
| \|      | or           |
| ()      | grouping     |
| []      | 문자 집합        |
| ^       | not          |
| ?:      | 찾지만 기억하지는 않음 |
  
![image](../../assets/images/or1.png)
 이 예제에서는 **| **연산자를 사용하여 **hi 또는 hello** 라는 단어를 검색한다. 검색 결과는 **group1번**으로 지정된다.
  
![image](../../assets/images/or2.png)
 이 예제는 **|** 연산자와 **()**을 사용하여 **Ya** 와 **ya**를 찾는 예제이다. y를 그룹화 하여 검색했기 때문에 검색 결과의 첫 문자는 **group1**이 되겠다. **group의 개념**은 **결과를 grouping 할 때** 사용한다.
  
![image](../../assets/images/group2.png)
  이 예제는 grouping에 대한 결과를 좀 더 이해하기 쉽도록 2가지 그룹으로 검색하였다. **hello와** **hi **는 **group1**, **there**는 **group2** 에 속한다.
  
![image](../../assets/images/brakets2.png)
 **[]** 는 문자열 검색에서 가장 많이 사용되는 keyword로 검색할 문자열의 종류를 지정한다. 이 예제에서는 **gray**, **grby**, **grcy**, **grdy**, **...** 를 검색한다. **[0-9]**, **[가-힣]**, **[a-Z]** 등의 표현을 주로 사용한다.
  
![image](../../assets/images/forget.png)  
 **()**내부의 **?:** keyword는 검색은 하지만 grouping은 하지 않아야 할 경우에 사용한다.
  
![image](../../assets/images/not_brakets.png)
 **[]** 내부의 **^** keyword는 **[]** 안의 문자열 이외의 문자를 검색하는 **not**을 의미한다.
  
## 수량자(Quantifiers) 지정
 찾을 문자열의 **반복 수량**을 설정하는 Keyword의 모음이다.

| Keyword    | 기능                     |
| ---------- | ---------------------- |
| ?          | 문자열 0번 이상 1번 이하 반복     |
| *          | 문자열 0번 이상 반복           |
| +          | 문자열 1번 이상 반복           |
| {n}        | 문자열 n번 반복              |
| {min,}     | 문자열 min번 이상 반복         |
| {min, max} | 문자열 min번 이상 max번 이하 반복 |
  
![image](../../assets/images/qeustionMark.png)
 이 예제는 **\***를 사용하여 **gry**, **gray**, **graay**, **graaay**, **...** 를 검색한다.
  
![image](../../assets/images/plus.png)
 이 예제는 **\+**를 사용하여 **gray**, **graay**, **graaay**, **...** 를 검색한다.
  
![image](../../assets/images/repeatNumber.png)
이 예제는 **{n}**을 사용하여 **graay**를 검색한다.
  
![image](../../assets/images/repeatMin%201.png)
이 예제는 **{min,}**을 사용하여 **graay**, **graaay**, **graaaay**, **...** 를 검색한다.
  
![image](../../assets/images/repeatMinMax.png)  
이 예제는 **{min, max}**을 사용하여 **gray**, **graay**를 검색한다.
  
## 경계범위(Boundary-type) 지정
 경계범위는 **문장**이나 **단어**에서 내가 **찾는 문자의 위치**를 지정하는 keyword의 모음 이다.
 
| keyword | 기능       |
| ------- | -------- |
| \b      | 단어 경계    |
| \B      | 단어 경계 아님 |
| ^       | 문장의 시작   |
| $       | 문장의 끝    |
  
![image](../../assets/images/b1.png)
 이 예제는 **\\b**를 사용하여 **단어의 시작**에 위치한 **Ya**를 검색한다.
  
![image](../../assets/images/b2.png)
 이 예제는 **\\b**를 검색 문자의 끝에 삽입하여 **단어의 끝**에 위치한 **Ya**를 검색한다.
  
![image](../../assets/images/bigB1.png)
 **\\B** 는 **\\b** 의 반대의미인 단어의 경계가 아닌 문자열 중 일치하는 대상을 검색한다. 이 예제는 **단어의 처음에 위치하지 않은 Ya**를 검색한다.
  
![image](../../assets/images/bigB2.png)
 이 예제는 **단어의 끝에 위치하지 않은 Ya**를 검색한다. 
  
![image](../../assets/images/angle1.png)
 **/gm** 검색옵션과 **^** 를 사용하여 **문장의 시작에 위치한 Ya**를 검색한다.
  
![image](../../assets/images/angle2.png)
 **/g** 검색 옵션과 **^** 를 사용하여 글 전체가 하나의 문장으로 간주된 상태에서 **문장의 시작에 위치한 Ya**를 검색한다.
  
![image](../../assets/images/dolar.png)
 **$** 를 사용하여 **문장의 끝에 위치한 Ya**를 검색한다. 
  
## 문자 클래스 지정
  검색할 **문자 타입**을 저장하는 keyword의 모음이다. **영문 키워드의 대소문자는 부정을 의미**한다.

| Keyword | 기능                |
| ------- | ----------------- |
| \       | 특수 문자 앞 prefix    |
| .       | 줄바꿈 문자를 제외한 모든 문자 |
| d       | 숫자                |
| D       | 숫자가 아닌 문자         |
| w       | word 문자           |
| W       | word 문자가 아닌 문자    |
| s       | 공백문자              |
| S       | 공백문자가 아닌 문자       |
  
![image](../../assets/images/backSlash.png)
 이 예제는 **\\. **을 사용하여 **.** 문자를 검색한다.
  
![image](../../assets/images/dot.png)
 이 예제는 **.**을 사용하여 **줄바꿈 문자를 제외한 모든 문자**를 검색한다.
  
![image](../../assets/images/digit.png)
 이 예제는 **\\d** 를 사용하여 **숫자**를 검색한다.
  
![image](../../assets/images/not_digit.png)
 이 예제는 **\\D**를 사용하여 **숫자를 제외한 모든 문자**를 검색한다.
  
![image](../../assets/images/word.png)
  이 예제는 **\\w**를 사용하여 **공백, 특수문자를 제외한 모든 문자**를 검색한다.
  
![image](../../assets/images/not_word.png)
 이 예제는 **\\W** 를 사용하여 **공백**, **특수문자**를 검색한다.
  
![image](../../assets/images/space.png)
 이 예제는 **\\s** 를 사용하여 **공백문자**만 검색한다.
  
![image](../../assets/images/not_space.png)  
 이 예제는 **\\S** 를 사용하여 **공백문자가 아닌 문자**를 검색한다.

 모든 실습 예제들은 [정규식테스트 웹 페이지](https://regexr.com/5mhou)에서 진행하였다. 정규식 입력은 물론이고, 사용자가 검색 대상 내용을 입력할 수 있으니 참고하면 좋을 듯 하다.

---
  
# 연결문서
- [정규식테스트 웹 페이지](https://regexr.com/5mhou)