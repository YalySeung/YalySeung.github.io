---
title : "Servlet"
excerpt : "Servlet"
toc : true
toc_sticky : true
toc_label : "Servlet"
categories:
- Spring
tags:
- [Spring]
last_modified_at: 2023-10-25T08:00:00-10:00:00
---

# 날짜 : 2023-10-25 15:50

# 태그 : #Spring
---

# 내용

## Servlet 이란
- 동적 웹페이지를 만들 때 사용되는 자바 기반의 웹 애플리케이션 프로그래밍 기술
- 웹 요청과 응답의 흐름을 간단한 메서드 호출만으로 처리할 수 있도록 해준다.

## 특징
- 사용자의 Request에 대해 동적으로 작동하는 웹 어플리케이션 컴포넌트
- Java Thread 사용
- MVC 패턴의 컨트롤러로 이용됨
- 컨테이너에서 실행됨
- 보안 기능 적용하기 쉬움

## 동작
![image](./../../assets/images/../../assets/Images/ServletProcess.png)

## Servlet Interface

```java
package javax.servlet;  
import java.io.IOException;  
  
public interface Servlet {  
    public void init(ServletConfig config) throws ServletException;  
    
    public ServletConfig getServletConfig();  
      
    public void service(ServletRequest req, ServletResponse res)  
   throws ServletException, IOException;  
    
    public String getServletInfo();  

    public void destroy();  
}
```

- Init() : 해당 서블릿이 메모리에 없을 경우 적재, 한번만 실행된다
- service() : 요청이 doGet 과 doPost로 분기
- destroy() : 종료시 처리해야 할 작업, 한번만 호출됨

---

# 연결문서
