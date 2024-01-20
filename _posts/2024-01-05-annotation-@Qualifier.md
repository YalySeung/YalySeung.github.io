---
title : "@Qualifier"
excerpt : "@Qualifier"
toc : true
toc_sticky : true
toc_label : "@Qualifier"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2024-01-05T08:00:00-10:00:00
---

# 날짜 : 2024-01-05 18:11

# 태그 : #Spring #Annotation
---

# 내용

## Artifact
- spring-beans

## 역할
- [@Autowired](../../annotation/annotation-@Autowired)로 연결한 bean 목록에서 유일한 bean을 구별

> **memo**
>
> Spring은 동일한 타입을 가진 bean 객체가 2개 존재할 경우 어떤 bean을 주입할지 알 수 없기때문에 Exception을 발생시킴
{: .notice--info}

## 사용법

### bean 선언

```java
@Bean 
@Qualifier("myWebClient") 
public class myWebClient implements WebClient {
	...
}
```

### Constructor Injection

```java
public class MyClass {
	private final WebClient webClient;
	
	@Autowired 
	public MyClass(@Qualifier("myWebClient") WebClient webClient) {
		this.webClient = webClient;
	}
}
```

### Setter Injection

```java
public class MyClass {
	private final WebClient webClient;
	
	@Autowired 
	public setWebClass(@Qualifier("myWebClient") WebClient webClient) {
		this.webClient = webClient;
	}
}
```

### Field Injection

```java
public class MyClass {
	@Autowired
	@Qualifier("myWebClient")
	private WebClient webClient;
}
```

---

# 연결문서
- [@Autowired](../../annotation/annotation-@Autowired)