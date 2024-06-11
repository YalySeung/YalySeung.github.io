---
title : "MockMVC"
excerpt : "MockMVC"
toc : true
toc_sticky : true
toc_label : "MockMVC"
categories:
- Spring
tags:
- [Spring, BackEnd, TDD, 미완료]
last_modified_at: 2023-12-14T08:00:00-10:00:00
---
  
---
  
## 정의
> **MockMVC란?**  
>
> Spring 3.2 부터  Spring MVC를 모킹하여 웹 어플리케이션 테스트를 지원하는 라이브러리로 Web Application을 배포하지 않고 Spring MVC의 동작을 재현하여 테스트 할 수 있다 
{: .notice--info}  
  
## Artifact
- org.springframework.test.web.servlet
  
## Initialize
  
### 방법 1. webAppContextSetup
- WebApplicationContext를 사용하여 테스트할 경우 사용
  
```java
MockMvc mockMvc;

@BeforeEach  
void setUp(WebApplicationContext wac) {  
    mockMvc = MockMvcBuilders.webAppContextSetup(wac).build(); 
}
```
  
### 방법 2. standaloneSetup
- 특정 컨트롤러만 테스트할 경우 사용
  
```java
MockMvc mockMvc;

@BeforeEach 
void setup() { 
	mockMvc = MockMvcBuilders.standaloneSetup(new ApiController()).build(); 
}
```
  
## Request Test
  
### perform()
  
```java
public ResultActions perform(RequestBuilder requestBuilder) throws Exception
```  
- Reqeust를 실행하는 Method
- perform()은 RequestBuilder를 Parameter로 받는데 [MockMvcRequestBuilders](#mockmvcrequestbuilders) 를 사용하여 손쉽게 MockHttpServletRequestBuilder 생성할 수있음
  
### MockMvcRequestBuilders
- RequestBuilder 객체를 생성하는 Static Methods를 제공
  
```java
public static MockHttpServletRequestBuilder get(String urlTemplate, Object... uriVars){...}

public static MockHttpServletRequestBuilder post(String urlTemplate, Object... uriVars){...}

public static MockHttpServletRequestBuilder put(String urlTemplate, Object... uriVars){...}

public static MockHttpServletRequestBuilder delete(String urlTemplate, Object... uriVars){...}
...
```
  
## assertion
  
### methods
  
#### MockMvcResultMatchers

| 메서드명                  | 검증 대상                               |
| --------------------- | ----------------------------------- |
| request               | session scope, request scope, async |
| handler               |                                     |
| model                 | spring MVC model status             |
| view                  | controller가 반환한 view 명              |
| flash                 |                                     |
| forwardedUrl          | 이동 대상의 경로                           |
| forwardedUrlTemplate  |                                     |
| forwardedUrlPattern   |                                     |
| redirectedUrl         |                                     |
| redirectedUrlTemplate |                                     |
| status                | status code                         |
| header                | response header                     |
| content               | response body                       |
| jsonPath              | body의 특정 값                          |
| xpath                 |                                     |
| cookie                |                                     |
  
---
  
# 연결문서
- [SpringMVC](../../spring/spring-SpringMVC)
- https://seongwon.dev/Spring-MVC/20220624-MockMvc%EB%9E%80/
- https://adjh54.tistory.com/347