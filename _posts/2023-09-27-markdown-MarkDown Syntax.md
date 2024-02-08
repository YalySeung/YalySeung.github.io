---
title : "MarkDown Syntax"
excerpt : "MarkDown Syntax"
toc : true
toc_sticky : true
toc_label : "MarkDown Syntax"
categories:
- Markdown
tags:
- [MarkDown, Syntax]
last_modified_at: 2023-09-27T08:00:00-10:00:00
---

# 날짜 : 2023-09-27 12:17

# 태그 : #MarkDown #Syntax
---

# 내용

## Syntax

### 중첩 구조 표현
```

- 대분류  
	- 중분류  
		- 소분류  

``` 
 - 대분류
	 - 중분류
		 - 소분류

### 헤더
```

## h1  

### h2  

#### h3  

##### h4  

###### h5  

####### h6  
```

## h1

### h2

#### h3

##### h4

###### h5

####### h6

### 순서 없는 리스트
```

- depth1  
  * depth2  
	+ depth3  
  * depth2  
- depth1  
```

- depth1
  * depth2
	+ depth3
  * depth2
- depth1

### 순서 있는 리스트
```
1. depth1_1
2. dqpth1_2
  1. depth2_1  
	- depth3_1  
	- depth3_2
  2. depth2_2  
	- depth3_3  
	- depth3_4
```

  1. depth1_1
  2. dqpth1_2
	  1. depth2_1  
		- depth3_1  
		- depth3_2
	  2. depth2_2  
		- depth3_3  
		- depth3_4

---

## 텍스트 스타일

### 텍스트 강조
```
**텍스트**
```

**텍스트**

### 텍스트 기울임
```
*텍스트*
```

*텍스트*

### 텍스트 굵고 기울임
```
***텍스트***
```

***텍스트***

### 텍스트 가로줄
```
~~텍스트~~
```

~~텍스트~~

### 텍스트 밑줄
```
<u>텍스트</u>
```

<u>텍스트</u>

### 텍스트 글자색
```
<span style="color:red">텍스트</span>
```

<span style="color:red">텍스트</span>

### 텍스트 개행
```
첫줄[공백][공백][개행문자]
둘째줄
```

첫줄  
둘째줄

### 텍스트 공백, 들여쓰기
```
전각 문자 사용! ==> (　)
```

  들여쓰기

## Inline 코드블럭
```

```c#
	using system;  
	class Sample{  
	  public Sample(){  
	
	  }  
	}
	```
```

```c#
using system;
class Sample{
  public Sample(){

  }
}
```
    스페이스바 4번으로도 가능

### 지원 언어

|      |            |
| ---- | ---------- |
| bash | java       |
| cs   | javascript |
| cpp  | php        |
| css  | perl       |
| diff | python     |
| http | ruby       |
| html | sql        |
| ini  | json       |

## 링크

### 일반 링크
```
<https://www.google.com>
```

  <https://www.google.com>

### 텍스트 링크
```
[구글페이지](https://www.google.com)
```

[구글페이지](https://www.google.com)

### 파일내에서 문단 이동
- 방법 
1. 헤더 제목 문자열 복사 후 (문단의 주소)에 복사
2. 특수문자 제거
3. 공백을 -로 변경
4. 대문자를 소문자로 변경

```
[Inline 코드블럭](#inline-코드블럭)
```

[Inline 코드블럭](#inline-코드블럭)

### 파일 간 이동
- 방법
1. 공백이 있을 경우 %20 으로 치환한다
```
[<링크텍스트>](<파일경로>)
```
[링크텍스트입니다.](./MarkDown%20Syntax.md)

## 이미지 사용

### 그림 삽입
```
![image](이미지주소){: width="20%" height="20%"}
```

![image](LinkImage.jpg){: width="20%" height="20%"}

### 그림 링크 삽입
```
\[![image](이미지 경로)](링크주소)
```
[![image](LinkImage.jpg)](#inline-코드블럭)

## 기타

### 인용문
```
>인용문
{: .notice--info}
  >>중첩 인용문
```
    
> 인용문
>> 중첩인용문
{: .notice--info}

### 주석
```
<cite>google</cite> --- google-forum' Conference, 1997
```

<cite>google</cite> --- google-forum' Conference, 1997

### 체크리스트
```

- [ ] 체크 안됨  
- [x] 체크 됨
```

- [ ] 체크 안됨
- [x] 체크 됨

### 구분선
```

---  
***
```

---
***

### 테이블
```
|제목|내용|설명|
|:---|---: |:---: |
|좌측정렬|우측정렬|가운데정렬|
|좌측정렬|**우측정렬 진하게**|가운데정렬|
|좌측정렬|<span style="color:red">우측정렬Red</span>|가운데정렬|
|좌측정렬|개행하고싶어\<br>다음내용|개행성공|
```

|제목|내용|설명|
|---|---|---|
|좌측정렬|우측정렬|가운데정렬|
|좌측정렬|**우측정렬 진하게**|가운데정렬|
|좌측정렬|<span style="color:red">우측정렬Red</span>|가운데정렬|
|좌측정렬|개행하고싶어<br>다음내용|개행성공|

### 접기 펼치기
```
<details>
<summary>클릭!</summary>
<div markdown="1">
까꿍
</div>
</details>
```

<details>
<summary>클릭!</summary>
<div markdown="1">
까꿍
</div>
</details>

### 버튼
```
<a href="#" class="click_button">Button</a>
```

<a href="#" class="click_button">Button</a>

### 각주
```
이글에는 각주가 있어요[^1]
[^1]: 각주의 정보는 이렇게 달아요
```

이글에는 각주가 있어요[^1]
[^1]: 각주의 정보는 이렇게 달아요

---

# 연결문서