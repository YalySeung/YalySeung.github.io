---
title : "html 문서 기본 구조"
excerpt : "html 문서 기본 구조"
toc : true
toc_sticky : true
toc_label : "html 문서 기본 구조"
categories:
- WebCommon
tags:
- [WebCommon, FrontEnd, html]
last_modified_at: 2023-10-12T08:00:00-10:00:00
---
  
---
  
## 샘플
  
```html
<!DOCTYPE html>  
{: .notice}  
<html lang="ko">  
{: .notice}  
	<head>  
{: .notice}  
		<meta charset="utf-8">  
{: .notice}  
		<title>여기에는 문서의 제목을 입력해주세요</title> 
{: .notice}  
	</head>  
{: .notice}  
	<body> 여기에 웹페이지에 표시할 콘텐츠(태그)를 입력해주세요 </body> 
{: .notice}  
</html> 
{: .notice}  
```
  
## \<DOCTYPE\> 
{: .notice}  
- 문서의 내용이 어떤 마크업 언어 형식으로 작성되었는지 명시
  
## \<html\> 
{: .notice}  
- 문서의 시작과 끝
- 실제 문서의 내용을 표시
  
## \<head\> 
{: .notice}  
- 브라우저에게 문서의 정보를 전달
- 웹 페이지 품질에 영향을 주는 정보
  
## \<meta\> 
{: .notice}  
- 문서의 키워드 또는 설정 등 문서와 관련된 항목들 지정
- ex ) charset
  
## \<title\> 
{: .notice}  
- 문서의 제목을 입력하는 태그
- 입력한 내용이 웹 브라우저 탭에 표시됨
  
## \<body\> 
{: .notice}  
- 웹 브라우저에 표시될 콘텐츠
- 텍스트, 미디어 요소, 이미지 등등

---
  
# 연결문서
- [html-작성법 기본](../../webcommon/webcommon-html-작성법-기본)