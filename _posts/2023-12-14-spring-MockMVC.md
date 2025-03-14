---
title : "MockMVC"
excerpt : "MockMVC"
toc : true
toc_sticky : true
toc_label : "MockMVC"
categories:
- Spring
tags:
- [Spring, BackEnd, TDD]
last_modified_at: 2023-12-14T08:00:00-10:00:00
---
  
---
  
> **MockMVC란?**  
>
>  Spring 3.2부터 Spring MVC를 모킹하여 웹 애플리케이션 테스트를 지원하는 라이브러리로, Web Application을 배포하지 않고 Spring MVC의 동작을 재현하여 테스트할 수 있다. 
{: .notice--info}  

  MockMVC를 사용하면 **실제 서버를 실행하지 않고도 컨트롤러 로직을 테스트할 수 있다.**
  
## Gradle 의존성 추가
  
```groovy
testImplementation 'org.springframework:spring-test:5.3.8'
```
  
## MockMVC 초기화 방법
  
### 1️⃣ Web Application Context를 사용하여 초기화
  `MockMvcBuilders.webAppContextSetup(wac).build();`를 사용하여 `MockMvc`를 초기화할 수 있다.
  
```java
MockMvc mockMvc;

@BeforeEach  
void setUp(WebApplicationContext wac) {  
    mockMvc = MockMvcBuilders.webAppContextSetup(wac).build(); 
}
```
  
### 2️⃣ 특정 컨트롤러만 테스트할 경우
  `MockMvcBuilders.standaloneSetup()`을 사용하여 개별 컨트롤러만 초기화할 수 있다.
  
```java
MockMvc mockMvc;

@BeforeEach 
void setup() { 
    mockMvc = MockMvcBuilders.standaloneSetup(new ApiController()).build(); 
}
```
  
## API 호출 테스트
  MockMVC의 `perform()` API를 사용하면 **실제 컨트롤러를 호출하는 것과 동일한 테스트가 가능**하다.
  
```java
public ResultActions perform(RequestBuilder requestBuilder) throws Exception
```
  
### 3️⃣ `MockMvcRequestBuilders`를 사용한 API 요청
  
```java
public static MockHttpServletRequestBuilder get(String urlTemplate, Object... uriVars){...}

public static MockHttpServletRequestBuilder post(String urlTemplate, Object... uriVars){...}

public static MockHttpServletRequestBuilder put(String urlTemplate, Object... uriVars){...}

public static MockHttpServletRequestBuilder delete(String urlTemplate, Object... uriVars){...}
```
  
## 응답 검증 (Assertion)
  
### 4️⃣ `MockMvcResultMatchers`를 활용한 검증
  
| 메서드명                  | 검증 대상                               |
| --------------------- | ----------------------------------- |
| request               | session scope, request scope, async |
| handler               |                                     |
| model                 | spring MVC model status             |
| view                  | controller가 반환한 view 명              |
| flash                 |                                     |
| forwardedUrl          | 이동 대상의 경로                           |
| redirectedUrl         | 리다이렉트된 URL 확인                     |
| status                | HTTP 상태 코드 검증                     |
| header                | 응답 헤더 확인                         |
| content               | 응답 본문 검증                         |
| jsonPath              | JSON 응답 데이터 확인                     |
  
### 5️⃣ JSON 응답 데이터 검증 예제
  `Hamcrest`를 활용하여 JSON 값을 검증할 수 있다.
  
```java
@Test  
void TestTestController()  {  
	mockMvc.perform(MockMvcRequestBuilders.get("/test"))  
            .andExpect(status().isOk())  
            .andExpect(jsonPath("$.error").value("false"))  
            .andExpect(jsonPath("$.count").value(matchesRegex("\d+")))
            .andExpect(jsonPath("$.datalist").isArray())  
            .andExpect(jsonPath("$.datalist", hasSize(greaterThan(0))))
            .andExpect(jsonPath("$.datalist[*].sequence", everyItem(matchesRegex("\d+"))))  
            .andExpect(jsonPath("$.datalist[*].processDateTime", everyItem(matchesRegex("\d{4}-\d{2}-\d{2} \d{2}:\d{2}:\d{2}")))) // 예: "2024-07-30 15:00:00"  
            .andExpect(jsonPath("$.datalist[*].userName", everyItem(matchesRegex("^[\p{L} ]+$")))); // 이름이 문자와 공백만 포함하도록 정규 표현식 설정
}
```
  
### 6️⃣ JSON Path 오류 해결을 위한 의존성 추가
  
```groovy
implementation 'com.jayway.jsonpath:json-path:2.7.0'
```

---
  
# 연결문서
- [SpringMVC](../../spring/spring-SpringMVC)
- [ResultActions](../../spring/spring-ResultActions)
- [Hamcrest](../../tdd/tdd-Hamcrest)
