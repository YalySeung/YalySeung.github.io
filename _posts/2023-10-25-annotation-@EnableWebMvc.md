---
title : "@EnableWebMvc"
excerpt : "@EnableWebMvc"
toc : true
toc_sticky : true
toc_label : "@EnableWebMvc"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2023-10-25T08:00:00-10:00:00
---
  
---
  
## Artifact
- **web.servlet**
  
## 역할
- @Configuration Annotation과 함께 쓰여 클래스가 Spring MVC의 구성요소중 하나임을 표기
- 스프링이 제공하는 웹과 관련된 bean들이 제공된다
  
## 사용법
  
```java
@Configuration  
@EnableWebMvc  
public class APIConfiguration implements WebMvcConfigurer {
	...
}
```

---
  
# 연결문서
- [SpringMVC](../../spring/spring-SpringMVC)
- [SpringMVC 구현](../../spring/spring-SpringMVC-구현)