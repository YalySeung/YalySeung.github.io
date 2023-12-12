---
title : "DOM"
excerpt : "DOM"
toc : true
toc_sticky : true
toc_label : "DOM"
categories:
- WebCommon
tags:
- [WebCommon, FrontEnd]
last_modified_at: 2023-12-08T08:00:00-10:00:00
---

# 날짜 : 2023-12-08 12:11

# 태그 : #WebCommon #FrontEnd 
---

# 내용

## 정의
> DOM이란?
> The Document Object Model
> HTML, XML 문서의 프로그래밍 인터페이스
> <span style="color:red">웹 브라우저가 HTML 페이지를 인식하는 방식</span>  

## 특징
- 프로그래밍 언어가 문서구조에 접근할 수 있는 방법 제공
- tree 구조로 각 Element를 관리

## 웹페이지(Document) 렌더링 프로세스
  
![image](./../../assets/images/HtmlToDoc.png)
- DOM : HTML 요소들을 구조화
- CCSOM(Cascading Style Sheets Object Model) : 요소들과 연관된 스타일 정보의 구조화
- Render Tree : 각 요소들을 트리구조화
- 이후 프로세스 : Tree를 Document로 렌더링

## DOM 에서 script의 사용
- 각 브라우저 별로 각각의 DOM 이 구현되어 있다.
- \<script\> 요소 사용

```xml
<head>
<title> DOM </title>
<script type= "text/javascript">
	//script 내용...
</script>
</head>
```

- window 또는 document elements를 위한 API 사용

```xml
<body onload="window.alert('welcome to my home page!');">
```

## node
- tree 구조에서 root 노드를 포함한 모든 개개의 개체
- head, body, script, h1 .... 등등

## 중요 개념

### Window
- 해당 창에 로드된 DOM 문서
- document.defaultView, window 속성으로 주어진 문서에 대한 창 접근 가능
- [Window interface 정보](https://developer.mozilla.org/ko/docs/Web/API/Window)

### Document
- 브라우저가 불러온 웹 페이지
- 페이지 콘텐츠의 진입점 역할 수행
- 모든 종류의 문서에 대한 공통의 속성과 메서드를 묘사
- document 속성으로 현재 페이지의 Document 접근 가능
- [Document interface 정보](https://developer.mozilla.org/ko/docs/Web/API/Document)

### Element
- Document 안의 모든 객체가 상속하는 범용적인 기반 클래스
- [Element class 정보](https://developer.mozilla.org/ko/docs/Web/API/Element)

## 웹페이지, XML 페이지 스크립팅에서 사용하는 공통 API
- document.getElementById(id) : 주어진 id를 가진 요소의 참조를 반환한다.
- document.getElementsByTagName(name) : 주어진 태그명을 갖는 요소의 목록을 반환한다
- document.createElement(name) : 주어진 태그명을 사용해 새로운 요소를 생성한다.
- parentNode.appendChild(node) : 부모 노드에 하위 노드를 추가한다.
- element.innerHTML : 요소 콘텐츠의 마크업을 나타낸다.
- element.setAttribute : 현재 노드의 명명된 속성 값을 설정한다.
- element.getAttribute : 현재 노드에서 명명된 속성의 값을 반환한다.
- element.addEventListener : 요소의 특정 이벤트 유형에 이벤트 처리기를 등록한다.

---

# 연결문서
- [html-문서 기본 구조](../../WebCommon/WebCommon-html-문서-기본-구조)
- [html-작성법 기본](../../WebCommon/WebCommon-html-작성법-기본)
- [html-tags](../../WebCommon/WebCommon-html-tags)