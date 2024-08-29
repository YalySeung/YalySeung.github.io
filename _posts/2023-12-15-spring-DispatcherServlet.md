---
title : "DispatcherServlet"
excerpt : "DispatcherServlet"
toc : true
toc_sticky : true
toc_label : "DispatcherServlet"
categories:
- Spring
tags:
- [Spring]
last_modified_at: 2023-12-15T08:00:00-10:00:00
---
  
---
  
## 정의
> **DispatcherServlet이란?**  
>
> HTTP 프로토콜로 들러오는 모든 요청을 가장 먼저 받아 적합한 컨트롤러에 위임해주는 Front Controller 
{: .notice--info}  
  
## 장점
- web.xml 역할 축소
- Contoller 구현만 하면, DispatcherServlet이 알아서 적합한 컨트롤러로 위임
  
## 구조
- 구조를 중요한 Field 기준으로 확인해보자
  
```java
private List<HandlerMapping> handlerMappings;
private List<HandlerAdapter> handlerAdapters;
private List<ViewResolver> viewResolvers;
private List<HandlerExceptionResolver> handlerExceptionResolvers;
private MultipartResolver multipartResolver;
private LocaleResolver localeResolver;
private ThemeResolver themeResolver;
```
  
### HandlerMapping
- 어떤 컨트롤러가 해당 요청을 처리 할 수 있을지 식별
  
### HandlerAdapter
- 컨트롤러의 구현 방식이 다양하기때문에 Dispatcher에서 직접 Controller를 호출하는 것이 아니라 HandlerAdapter를 통해 위임
  
### ViewResolver
- Response가 화면일 경우 View 이름에 맞는 View를 찾아 반환해주는 역할
  
### HandlerExceptionResolver
- Controller 밖으로 Throw 된 예외를 해결하고 동작방식을 변경
- 예외 발생시 보여줄 ModelAndView 설정
  
### MultipartResolver
- 파일 업로드와 같은 Multipart 요청을 처리하기 위한 인터페이스
- 클라이언트로부터 전송된 HTTP 요청에서 Multipart 데이터를 읽고 해석하는 기능 제공
  
#### 사용방법
- MultipartResolver Bean을 등록한다.
  
```java
@Bean  
public MultipartResolver multipartResolver(  
        @Value("#{Properties['common.file.maxUploadSizePerFile']}") Long maxUploadSizePerFile) {  
    CommonsMultipartResolver multipartResolver = new CommonsMultipartResolver();  
    multipartResolver.setMaxUploadSize(-1); // no limit  
    multipartResolver.setMaxUploadSizePerFile(maxUploadSizePerFile);  
    return multipartResolver;  
}
```
  
### LocaleResolver
- 국제화 기능을 구현하기 위해서 어떤 언어로 페이지를 보여줄지 설정
  
#### 사용방법
- LocaleResolver Bean 을 등록한다.
  
```java
@Bean  
public LocaleResolver localeResolver() {  
	return new AcceptHeaderLocaleResolver();  
}  
```
  
### ThemeResolver
- 페이지에서 사용할 테마를 설정

---
  
# 연결문서
- [WebMvcConfigurer](../../spring/spring-WebMvcConfigurer)
- [SpringMVC](../../spring/spring-SpringMVC)