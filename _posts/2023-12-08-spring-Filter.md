---
title : "Filter"
excerpt : "Filter"
toc : true
toc_sticky : true
toc_label : "Filter"
categories:
- Spring
tags:
- [Spring]
last_modified_at: 2023-12-08T08:00:00-10:00:00
---

# 날짜 : 2023-12-08 12:18

# 태그 : #Spring 
---

# 내용

## 특징
- DispatcherServlet에 요청이 전달되지 전, 후에 url 패턴에 맞는 모든 요청에 대한 처리
- 스프링과 무관하게 전역적으로 처리해야 할 작업 수행
- ServletRequest/ServletResponse 객체를 조작 가능
- 웹 컨테이너에 의해 관리됨
- chain.doFilter 메서드 호출로 다음 Filter 연결
- ex) 보안, 인코딩, 로깅, 데이터 압축

## 예시

### web.xml

```xml
...
<filter>
  <filter-name>SampleFilter1</filter-name>
  <filter-class>필터패키지 경로.SampleFilter1</filter-class>        
</filter>
<filter-mapping>
  <filter-name>SampleFilter1</filter-name>
  <url-pattern>/*</url-pattern>
</filter-mapping>

<filter>
  <filter-name>SampleFilter2</filter-name>
  <filter-class>필터패키지 경로.SampleFilter2</filter-class>        
</filter>
<filter-mapping>
  <filter-name>SampleFilter2</filter-name>
  <url-pattern>/*</url-pattern>
</filter-mapping>
...
```

### SampleFilter1

```java
public class SampleFilter1 implements Filter{
	public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) throws IOException, ServletException {
		// 처리할 로직...
	
		chain.doFilter(request, response);
	}
}
```

---

# 연결문서
