---
title : "WebApplicationInitializer"
excerpt : "WebApplicationInitializer"
toc : true
toc_sticky : true
toc_label : "WebApplicationInitializer"
categories:
- Spring
tags:
- [Spring, 미완료]
last_modified_at: 2024-05-01T08:00:00-10:00:00
---
  
---
  
## 정의
> **WebApplicationInitializer란?**  
>
> servlet 3.0 버전 이후, web.xml 없이 servlet context 초기화 작업을 도와주는 API  
{: .notice--info}  
  
## Gradle 설정
  
```groovy
dependencies {  
    implementation 'org.springframework:spring-web:5.3.22'  
    implementation 'javax.servlet:javax.servlet-api:4.0.1'
}
```
  
## Example
- WebApplicationInitializer 구현 Class 선언
- onStartup 메서드 구현
  
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

---
  
# 연결문서
- [WebMvcConfigurer](../../spring/spring-WebMvcConfigurer)