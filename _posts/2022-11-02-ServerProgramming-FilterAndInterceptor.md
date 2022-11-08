---
title: "Filter / Interceptor"
excerpt: "Client Request 전처리기"

categories:
- ServerProgramming

tags:
- [ServerProgramming]

toc: true
toc_sticky: true
toc_label: "Filter / Interceptor"

last_modified_at: 2022-11-08T08:00:00-10:00:00
---
# Spring MVC Life Cycle
  ![image](/assets/images/ServerProgramming/SpringMVCLifeCycle.png)

# Filter
  - DispatcherServlet에 요청이 전달되지 전, 후에 url 패턴에 맞는 모든 요청에 대한 처리
  - 스프링과 무관하게 전역적으로 처리해야 할 작업 수행
  - ServletRequest/ServletResponse 객체를 조작 가능
  - 웹 컨테이너에 의해 관리됨
  - chain.doFilter 메서드 호출로 다음 Filter 연결
  - ex) 보안, 인코딩, 로깅, 데이터 압축

## 예시
  - Web.xml
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

  - SampleFilter1 class
  ```java
    public class SampleFilter1 implements Filter{
      public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) throws IOException, ServletException {
              // 처리할 로직...

              chain.doFilter(request, response);
      }
    }
  ```

# Interceptor
  - 클라이언트 요청과 관련된 전역적 처리 작업 수행
  - ServletRequest/ServletResponse 객체 조작 불가
  - 스프링 컨테이너에 의해 관리됨
  - ex) 인증, JWT 토큰