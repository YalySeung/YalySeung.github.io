---
title : "@RequestMapping"
excerpt : "@RequestMapping"
toc : true
toc_sticky : true
toc_label : "@RequestMapping"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2023-11-05T08:00:00-10:00:00
---
  
---
  
## Gradle 설정
  
```groovy
dependencies {  
    implementation 'org.springframework:spring-web:5.3.22'
}
```
  
## 역할
- 특정 url 요청을 받아 어떤 Controller에서 처리할 지 정의하는 Annotation
  
## 속성
  
|이름|타입|설명|
|---|---|---|
|value|String[]|연결할 url|
|method|RequestMethod[]|HTTP Request 메소드|
|params|String[]|HTTP Request 파라미터를 Mapping 조건 부여|
|consumes|String[]|설정과 Context-Type request 헤더라 일치할 경우 사용|
|produces|String[]|설정과 Accept request 헤더가 일지할 경우에만 URL 호출|
  
## 사용법
- class와 method 에 사용 가능
  
```java
@RequestMapping({"/hello", "/hello-buddy", "/hello/**"}
public class TestController {  
	...
}
				
@RequestMapping(method = RequestMethod.GET, value = "/hello")
public class TestController {  
	...
}
```

---
  
# 연결문서
