---
title : "CORS"
excerpt : "CORS"
toc : true
toc_sticky : true
toc_label : "CORS"
categories:
- ServerCommon
tags:
- [SpringBoot, ServerCommon]
last_modified_at: 2025-03-27T08:00:00-10:00:00
---
  
---
  
> **CORS란?**  
>
> Cross-Origin Resource Sharing의 약어로, 웹 애플리케이션이 다른 출처(Origin)의 서버에 리소스를 요청할 때 브라우저가 리소스 접근을 제한하는 보안 정책이다. 
{: .notice--info}  

출처는 프로토콜, 도메인, 포트로 구성되며, 이 중 하나라도 다르면 다른 출처로 간주되어 CORS 에러가 발생한다.

---
  
## 📌 Spring Boot에서의 CORS 처리 방법

Spring Boot 환경에서는 크게 두 가지 방법으로 CORS를 설정할 수 있다.
  
### 🎯 필터를 이용한 방법
  
```java
@Component  
@Order(Ordered.HIGHEST_PRECEDENCE)  
public class CorsFilter implements Filter {  
  
    @Override  
    public void doFilter(ServletRequest req, ServletResponse res, FilterChain chain) throws IOException, ServletException {  
        HttpServletRequest request = (HttpServletRequest) req;  
        HttpServletResponse response = (HttpServletResponse) res;  

        response.setHeader("Access-Control-Allow-Origin", "*");
        response.setHeader("Access-Control-Allow-Credentials", "true");  
        response.setHeader("Access-Control-Allow-Methods","*");  
        response.setHeader("Access-Control-Max-Age", "3600");  
        response.setHeader("Access-Control-Allow-Headers",  
                "Origin, X-Requested-With, Content-Type, Accept, Authorization");  
  
        if("OPTIONS".equalsIgnoreCase(request.getMethod())) {  
            response.setStatus(HttpServletResponse.SC_OK);  
        }else {  
            chain.doFilter(req, res);  
        }  
    }  
}
```
  
### 🎯 Config 클래스를 이용한 방법 (권장)

보다 Spring Boot스럽게 Config를 이용하여 CORS 설정을 하는 방법이다.
  
```java
@Configuration
public class WebConfig implements WebMvcConfigurer {

    @Override
    public void addCorsMappings(CorsRegistry registry) {
        registry.addMapping("/**")
                .allowedOrigins("*") // 특정 도메인을 명시할 수도 있음
                .allowedMethods("GET", "POST", "PUT", "DELETE", "OPTIONS")
                .allowedHeaders("*")
                .allowCredentials(true)
                .maxAge(3600);
    }
}
```

이 방법은 설정 클래스 하나로 깔끔하게 관리할 수 있으며 Spring Boot에서 가장 권장하는 방식이다.

---
  
## 📌 Config 방식을 사용할 때 장점
- 코드가 간결하고 명확해 유지보수가 쉬움
- 스프링의 기본 설정 방식과 잘 어울림
- 여러 경로에 서로 다른 CORS 정책을 쉽게 설정 가능

---
  
## 📌 주의사항
- 운영 환경에서는 "\*" 사용 대신 허용할 특정 Origin만 명시할 것
- credentials 허용 시 "\*" 설정 불가, 명확한 도메인 지정 필요

---
  
## 📌 연결 문서