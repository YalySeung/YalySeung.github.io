---
title : "SpringMVC"
excerpt : "SpringMVC"
toc : true
toc_sticky : true
toc_label : "SpringMVC"
categories:
- Spring
tags:
- [Spring]
last_modified_at: 2023-10-25T08:00:00-10:00:00
---

# 날짜 : 2023-10-25 15:49

# 태그 : #Spring 
---

# 내용

## MVC란
- Model, View, Controller
- 애플리케이션을 각 역할에 맞게 분리하여 코드를 작성하는 방식

### Model
- 작업 처리 결과 데이터

### view
- Model을 이용하여 웹 브라우저와 같은 애플리케이션을 화면에 보이는 리소스
- html, pdf, excel, xml, json  등등

### Controller
- 사용자의 요청을 직접적으로 전달받는 Endpoint 로서 Model과 View간 상호작용을 해주는 역할

## Spring MVC란
- Spring에서 제공하는 웹 모듈을 포함하는 프레임웍

## Spring MVC 구조
  
![image](../../assets/images/SpringMVCProcess.png)

### DispatcherServlet
- request를 처리할 Controller 를 배정
- 결과 View를 user에게 전달
- 서블릿으로 등록하며, 모든 경로에 urlPatterns="/" 매핑

### Handler
- Controller
- http request 메시지를 처리해 필요한 데이터를 정제하여 Model에 저장
- 결과를 보여줄 View Name 지정

### ModelAndView
- Model 데이터와 View Name이 Wrapping된 객체

### ViewResolver
- View Name으로 반환할 View를 탐색
- View에 Model 데이터를 삽입

---

# 연결문서
- [SpringMVC 구현](../../spring/spring-SpringMVC-구현)
- [Servlet](../../spring/spring-Servlet)
- [DispatcherServlet](../../spring/spring-DispatcherServlet)