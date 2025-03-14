---
title : "WebApplicationInitializer"
excerpt : "WebApplicationInitializer"
toc : true
toc_sticky : true
toc_label : "WebApplicationInitializer"
categories:
- Spring
tags:
- [Spring]
last_modified_at: 2024-05-01T08:00:00-10:00:00
---
  
---
  
## 정의
> **WebApplicationInitializer란?**  
>
>  Servlet 3.0 버전 이후, `web.xml` 없이 Servlet Context 초기화 작업을 도와주는 API이다. 
{: .notice--info}  

  `WebApplicationInitializer`를 사용하면 **기존의 `web.xml` 없이 Java 기반 설정으로 서블릿 환경을 구성할 수 있다.**
  
## Gradle 설정
  
```groovy
dependencies {  
    implementation 'org.springframework:spring-web:5.3.22'  
    implementation 'javax.servlet:javax.servlet-api:4.0.1'
}
```
  
## Example
  
### 1️⃣ `WebApplicationInitializer` 구현 클래스 선언
  `onStartup()` 메서드를 오버라이드하여 서블릿을 등록한다.
  
```java
public class ApplicationInitializer implements WebApplicationInitializer {  
    @Override  
    public void onStartup(ServletContext servletContext) throws ServletException {  
        AnnotationConfigWebApplicationContext apiContext = new AnnotationConfigWebApplicationContext();  
        apiContext.register(APIConfiguration.class);  

        DispatcherServlet apiDispatcherServlet = new DispatcherServlet(apiContext);  

        ServletRegistration.Dynamic apiDispatcher = servletContext.addServlet("apiDispatcher", apiDispatcherServlet);  
        apiDispatcher.addMapping("/*");  
    }  
}
```
  
## 장점과 단점
  
### ✅ 장점
- **XML 설정 없이 Java 코드만으로 서블릿 초기화 가능**  
- **Spring Boot와의 호환성이 높아 유지보수 용이**  
  
### ❌ 단점
- **기존 XML 기반 설정을 사용하는 프로젝트에서는 전환 비용이 발생**  
- **Servlet 3.0 이상에서만 사용 가능**  

---
  
# 연결문서
- [WebMvcConfigurer](../../spring/spring-WebMvcConfigurer)
