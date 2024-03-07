---
title : "Message Converter"
excerpt : "Message Converter"
toc : true
toc_sticky : true
toc_label : "Message Converter"
categories:
- Spring
tags:
- [Spring]
last_modified_at: 2024-03-04T08:00:00-10:00:00
---

# 날짜 : 2024-03-04 21:18

# 태그 : #Spring
---

# 내용

## 정의
> **Message Converter란?**
>
> Spring MVC에서 요청 및 응답 메시지를 변환하는 인터페이스
> HTTP  요청과 응답의 body를 자바객체로 변환, 자바 객체를 다양한 메시지로 변환 등의 역할을 수행
{: .notice--info}

## 설정 방법
- configureMessageConverters 메서드를 Override 하여, converter 추가

```java
@Configuration  
@EnableWebMvc  
@ComponentScan(basePackages = "org.infinity.server.controller.api")  
public class APIConfiguration implements WebMvcConfigurer {  
    @Override  
    public void configureMessageConverters(List<HttpMessageConverter<?>> converters) {  
        GsonHttpMessageConverter converter = new GsonHttpMessageConverter();  
        converters.add(converter);  
    }  
}
```

> **caution**
>
> 여러 MessageConverter가 동일한 데이터를 처리할 경우 충돌이 발생할 수 있으므로, 우선순위를 조정해야 한다.
{: .notice--danger}

## 종류

| Converter명                           | 기능                                             |
| ------------------------------------ | ---------------------------------------------- |
| MappingJackson2HttpMessageConverter  | Jackson 라이브러리를 사용하여 java객체 <-> Json 객체 변환      |
| GsonHttpMessageConverter             | Gson 라이브러리를 사용하여 java객체 <-> Json 객체 변환         |
| StringHttpMessageConverter           | 문자열 데이터 처리, 주로 text/plain 타입에 사용               |
| ByteArrayHttpMessageConverter        | byte 배열 처리를 위한 컨버터, 이미지나 다른 바이너리 데이터를 전송할 때 사용 |
| FormHttpMessageConverter             | HTML Form 데이터 처리, HTML Form <-> Map 변환         |
| Jaxb2RootElementHttpMessageConverter | XML 데이터 처리, Java <-> XML                       |
| SourceHttpMessageConverter           | XML Source 객체 처리, 주로 XML 데이터를 처리할 때 사용         |
| BufferedImageHttpMessageConverter    | BufferedImage 객체 처리, 주로 이미지를 전송할 때 사용          |
| ResourceHttpMessageConverter         | String Resource 객체 처리, 주로 파일 다운로드에 사용          |
| AtomFeedHttpMessageConverter         | Atom 피드를 처리, Atom 피드를 생성하거나 파싱할 때 사용           |
| RssChannelHttpMessageConverter       | RSS 채널을 처리, RSS 채널을 생성하거나 파싱할 때 사용             |

---

# 연결문서
