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
  
> **MockMVC란?**  
>
> Spring 3.2 부터  Spring MVC를 모킹하여 웹 어플리케이션 테스트를 지원하는 라이브러리로 Web Application을 배포하지 않고 Spring MVC의 동작을 재현하여 테스트 할 수 있다 
{: .notice--info}  

 먼저 Mock MVC를 초기화 하는 방법을 살펴보자. Web Application Context를 사용하여 테스트할 경우와 특정 Controller만 테스트 할 때 초기화 하는 방법이 다르다.

 **Web Application Context를 사용하여 테스트** 할 경우에는 아래와 같이 초기화 메서드에서 매개변수로 받아와 **MockMVC에 주입**한다.
  
```java
MockMvc mockMvc;

@BeforeEach  
void setUp(WebApplicationContext wac) {  
    mockMvc = MockMvcBuilders.webAppContextSetup(wac).build(); 
}
```

 **특정 Controller만 테스트**하고 싶을 경우에는 **MockMvcBuilders**에서 제공하는 standaloneSetup 메서드를 사용한다.
  
```java
MockMvc mockMvc;

@BeforeEach 
void setup() { 
	mockMvc = MockMvcBuilders.standaloneSetup(new ApiController()).build(); 
}
```

 초기화를 마쳤다면 각 테스트에서 API 호출 테스트를 진행해보자. 우리가 사용할 API는 MockMvc가 제공하는 **perform API**이다. MockMvc에는 Application Context나 Controller 정보가 주입 되었으므로 **실제 컨트롤러를 호출하는 것과 동일한 테스트가 가능**하다. 
  
```java
public ResultActions perform(RequestBuilder requestBuilder) throws Exception
```

 perform() API는 RequestBuilder를 Parameter로 받는데 [MockMvcRequestBuilders](#mockmvcrequestbuilders) 를 사용하여 손쉽게 MockHttpServletRequestBuilder를 생성하여 사용할 수 있다.

 MockHttpServletRequestBuilder에서 제공하는 static 메서드는 아래와 같다.
  
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
  
```java
@Test  
void TestTestController()  {  

	mockMvc.perform(MockMvcRequestBuilders.get("/test"))  
            .andExpect(status().isOk())  
            .andExpect(jsonPath("$.error").value("false"))  
	        .andExpect(jsonPath("$.count").value(matchesRegex("\\d+")))
	        .andExpect(jsonPath("$.datalist").isArray())  
			.andExpect(jsonPath("$.datalist[*].sequence", everyItem(matchesRegex("\\d+"))))  
			.andExpect(jsonPath("$.datalist[*].processDateTime", everyItem(matchesRegex("\\d{4}-\\d{2}-\\d{2} \\d{2}:\\d{2}:\\d{2}")))) // 예: "2024-07-30 15:00:00"  
			.andExpect(jsonPath("$.datalist[*].userName", everyItem(matchesRegex("^[\\p{L} ]+$")))); // 이름이 문자와 공백만 포함하도록 정규 표현식 설정
}
```

 위 예시는 reponse에 대한 Json 파라미터를 하나씩 검증하는 것을 보여준다.

---
  
# 연결문서
- [SpringMVC](../../spring/spring-SpringMVC)
- [ResultActions](../../spring/spring-ResultActions)
- https://seongwon.dev/Spring-MVC/20220624-MockMvc%EB%9E%80/
- https://adjh54.tistory.com/347