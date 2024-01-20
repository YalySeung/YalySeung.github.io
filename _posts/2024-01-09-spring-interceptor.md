---
title : "interceptor"
excerpt : "interceptor"
toc : true
toc_sticky : true
toc_label : "interceptor"
categories:
- Spring
tags:
- [Spring]
last_modified_at: 2024-01-09T08:00:00-10:00:00
---

# 날짜 : 2024-01-09 13:42

# 태그 : #Spring 
---

# 내용

## 역할
- Spring이 제공하는 기술
- [DispatcherServlet](../../spring/spring-DispatcherServlet)이 컨트롤러를 호출하기 전과 후에 요청과 응답을 참조하거나 가공

## 사용방법

### Interceptor 정의

```java
public class DataSourceInterceptor implements HandlerInterceptor {  
  
    @Override  
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler)  
            throws Exception {  
        // 원하는 로직에 따라 데이터 소스 키를 선택합니다.  
        if (request.getRequestURL().toString().contains("/dev")) {  
            System.out.println("/dev");  
            DataSourceContextHolder.setDataSourceKey("devDataSource");  
        } else {  
            System.out.println("/prod");  
            DataSourceContextHolder.setDataSourceKey("prodDataSource");  
        }  
        return true;  
    }  
  
    @Override  
    public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView) throws Exception {  
  
    }  
    @Override  
    public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex)  
            throws Exception {  
        DataSourceContextHolder.clearDataSourceKey();  
    }  
}
```

### WebMvcConfigurerAdapter 에 Interceptor 등록

``` java
public class RpaViewWebMvcConfiguration extends WebMvcConfigurerAdapter {  
	...
  
    @Override  
    public void addInterceptors(InterceptorRegistry registry){  
        registry.addInterceptor(new DataSourceInterceptor()).addPathPatterns("/**");  
    }  
}
```

---

# 연결문서
- [SpringMVC](../../spring/spring-SpringMVC)