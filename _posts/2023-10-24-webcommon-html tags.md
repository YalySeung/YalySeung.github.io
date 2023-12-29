---
title : "html tags"
excerpt : "html tags"
toc : true
toc_sticky : true
toc_label : "html tags"
categories:
- WebCommon
tags:
- [WebCommon, html, FrontEnd]
last_modified_at: 2023-10-24T08:00:00-10:00:00
---

# 날짜 : 2023-10-24 12:14

# 태그 : #WebCommon #html #FrontEnd
---

# 내용

# 태그별 사용법

### h1,h2,h3...
- 헤드라인을 구성할 때 사용

```html
<h1>h1입니다.</h1>
<h2>h2입니다.</h2>
<h3>h3입니다.</h3>
<h4>h4입니다.</h4>
<h5>h5입니다.</h5>
<h6>h6입니다.</h6>
```

### p
- Paragraph(문단)

```html
<p>Geckos are a group of usually small, usually nocturnal lizards. They are found on every continent except Antarctica.</p>
```

### br
- break(줄바꿈)

```html
<p> O’er all the hilltops<br>
    Is quiet now,<br>
</p>
```

### hr
- horizontal rule(가로선)

```html
<p>1: The first rule of Fight Club is: You do not talk about Fight Club.</p>
<hr>
<p>2: The second rule of Fight Club is: Always bring cupcakes.</p>
```

### li
- 목록

#### ol
- ordered list

```html
<ol>
  <li>목록 1</li>
  <li>목록 2</li>
</ol>
```

#### ul
- unordered list

```html
<ul>
  <li>목록 1</li>
  <li>목록 2</li>
</ul>
```

### img
- image

```html
<img src="이미지 파일 경로" alt="대체용 텍스트">
```

### a
- anchor
- 다른 콘텐츠와 연결되는 하이퍼 링크 또는 링크

```html
<p><a href="~">표시 텍스트</a></p>
```

### div
- 컨텐츠들을 어떤 목적에 따라 묶을때 사용
- block label element(줄바꿈 O)

### span
- 컨텐츠들을 어떤 목적에 따라 묶을때 사용
- inline level element(줄바꿈 X)

### script
- javascript 코드 삽입

### link
- 외부 파일을 연결

### style
- 스타일 정보 정의

### input
- form 요소중 하나로 사용자가 정보를 입력하는 부분 정의

#### 속성

|속성명|설명|
|---|---|
|readonly|읽기전용 필드로 설정|
|placeholder|배경글|
|autofocus|페이지 로드 되자마자 마우스 커서 표기|
|autocomplete|자동완성|
|max/min|필등의 최대 최솟값 지정|
|maxLength|입력 문자 최대 길이|
|step|숫자 간격 설정(타입이 date, datetime, datetime-local, week, time, number, range 일 경우에만 사용)|
|required|필수 입력 지정|

##### type

|타입명|설명|
|---|---|
|hidden|사용자에게 숨김|
|text|텍스트 박스|
|search|검색 박스|
|tel|전화번호|
|url|url 주소|
|email| 이메일 주소|
|password|비밀번호|
|number|숫자, 우측에 화살표 포함|
|range|슬라이드 막대|
|color|색상표|
|checkbox|체크박스|
|radio|라디오버튼|
|datetime|국제 표준시로 설정된 날짜와 시간(년 월 일 시 분 초 분할초)|
|datetime-local|사용자가 위치한 지역 기준 날짜와 시간(년 월 일 시 분 초 분할초)|
|date|사용자가 위치한 지역 기준 날짜(년 월 일)|
|month|사용자가 위치한 지역 기준 날짜(년 월)|
|week|사용자가 위치한 지역 기준 날짜(년 주)|
|time|사용자가 위치한 지역 기준 시간(시 분 추 분할 초)|
|button|버튼|
|file|파일 첨부 버튼|
|submit|서버 전송|
|image|이미지|
|reset|리셋|

### form
- form 요소

#### 속성

|속성명|설명|
|---|---|
|method|전송 방식(get/port)|
|name|form 식별자|
|action|form을 전송할 서버쪽 script 파일 지정|
|target|action에서 지정한 script파일을 현재 창이 아닌 다른위치에 열도록 지정|

### iframe
- 외부 페이지 삽입
- 웹 페이지 안에 다른 웹 페이지 삽입

### nav
- 문서 연결 링크

### strong
- 중요 내용 강조

### button
- form 요소중 하나 

### aside
- 본문 이외의 내용

---

# 연결문서
- [html-작성법 기본](../../webcommon/webcommon-html-작성법-기본)
- [html-문서 기본 구조](../../webcommon/webcommon-html-문서-기본-구조)