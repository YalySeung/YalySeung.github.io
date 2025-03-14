---
title : "ObjectMapper"
excerpt : "ObjectMapper"
toc : true
toc_sticky : true
toc_label : "ObjectMapper"
categories:
- java
tags:
- [java]
last_modified_at: 2024-07-29T08:00:00-10:00:00
---
  
---
  
 이 글에서는 java에서 JSON을 다룰 때, 편하게 개발할 수 있도록 도와주는 ObjectMapper Class에 대해 알아보겠다.

> **ObjectMapper란?**  
>
> Jackson 라이브러리에서 제공하는 Class로, java 객체와 JSON 간 직렬화 및 역직렬화에 사용한다. 
{: .notice--info}  

 먼저 Jackson ObjectMapper 사용을 위해서는 프로젝트에 의존성을 추가해야한다.
  
```groovy
implementation 'com.fasterxml.jackson.core:jackson-databind:2.12.3'
```
  
## 주요 메서드
  
| 메서드 명                                            | 기능                                       |
| ------------------------------------------------ | ---------------------------------------- |
| writeValueAsString(Object value)                 | Java 객체를 JSON 문자열로 변환                    |
| writeValueAsBytes(Object value)                  | Java 객체를 JSON 바이트 배열로 변환                 |
| writeValue(File resultFile, Object value)        | Java 객체를 JSON 형식으로 파일에 Write             |
| writeValue(OutputStream out, Object value)       | Java 객체를 JSON 형식으로 출력 Stream에 Write      |
| writeValue(Writer writer, Object value)          | Java 객체를 JSON 형식으로 Writer 객체에 Write      |
| readValue(String content, Class\<T\> valueType)  | JSON 문자열을 T Class 타입의 객체로 변환             |
| readValue(byte[] src, Class\<T\> valueType)      | JSON Byte 배열을 T Class 타입의 객체로 변환         |
| readValue(File src, Class\<T\> valueType)        | 파일에서 읽은 JSON 문자열을 T Class 타입의 객체로 변환     |
| readValue(InputStream src, Class\<T\> valueType) | 입력 스트림에서 읽은 JSON 문자열을 T Class 타입의 객체로 변환 |
| readValue(Reader src, Class\<T\> valueType)      | Reader에서 읽은 JSON 문자열을 T Class 타입의 객체로 변환 |

 아래 소스코드는 java 객체를 JSON String으로 변환하여 API 를 호출하는 샘플 코드이다.
  
```java
@Test  
void getEchoUserInfo() throws Exception {  
    //given  
    String requestBody = objectMapper.writeValueAsString(TestResponse.builder()  
            .name("홍길동")  
            .registrationNumber("010-3333-3333")  
            .build());  
  
    //when  
  
    //then   
     mockMvc.perform(  
                    MockMvcRequestBuilders.post("/test/json/withbody")  
                            .contentType(MediaType.APPLICATION_JSON)  
                            .content(requestBody)  
            )  
            .andExpect(status().isOk())  
            .andExpect(content().json(requestBody));  
}
```

 간단하게 API 호출 하나만으로 Object 와 JsonString 간 변환이 가능함을 확인할 수 있다.

---
  
# 연결문서