---
title : "Filter"
excerpt : "Filter"
toc : true
toc_sticky : true
toc_label : "Filter"
categories:
- Spring
tags:
- [Spring, Servlet, Filter]
last_modified_at: 2023-12-08T08:00:00-10:00:00
---
  
---
  
## 📌 Filter란?

> **info**
>
> 필터(Filter)는 J2EE 표준 기능으로, **요청(Request)이 DispatcherServlet에 도달하기 전/후에 실행되어 공통 작업을 처리**할 수 있게 해주는 웹 컴포넌트이다.  
> 스프링 MVC 내부 컴포넌트가 아니며, **서블릿 컨테이너 레벨에서 동작**한다. 
{: .notice--info}  

---
  
## ✅ 주요 특징

- 전역 요청 전처리/후처리를 담당
- 모든 URL 요청에 대해 처리 가능 (`url-pattern`)
- 스프링 DispatcherServlet 앞단에서 동작
- `ServletRequest`, `ServletResponse` 직접 조작 가능
- 전처리 후 `chain.doFilter()`로 다음 필터 또는 서블릿에 연결

---
  
## ✅ 사용 예시 (web.xml 기반)
  
```xml
<filter>
  <filter-name>SampleFilter1</filter-name>
  <filter-class>com.example.SampleFilter1</filter-class>        
</filter>
<filter-mapping>
  <filter-name>SampleFilter1</filter-name>
  <url-pattern>/*</url-pattern>
</filter-mapping>
```
  
```java
public class SampleFilter1 implements Filter {
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain)
        throws IOException, ServletException {

        // 요청 전 처리 로직...
        chain.doFilter(request, response);
        // 응답 후 처리 로직...
    }
}
```

---
  
## ✅ Spring Boot 환경에서 사용

Spring Boot에서는 `@Component` 또는 `@Bean`으로 등록 가능하며, `FilterRegistrationBean`을 통해 우선순위 설정도 가능하다.
  
```java
@Component
@Order(Ordered.HIGHEST_PRECEDENCE)
public class LoggingFilter implements Filter {
    @Override
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain)
        throws IOException, ServletException {

        HttpServletRequest req = (HttpServletRequest) request;
        System.out.println("Request URI: " + req.getRequestURI());

        chain.doFilter(request, response);
    }
}
```

---

---
  
# 연결문서
- [SpringMVC](../../spring/spring-SpringMVC)
- [Servlet](../../spring/spring-Servlet)
- [RequestBodyLogging](../../spring/spring-RequestBodyLogging)