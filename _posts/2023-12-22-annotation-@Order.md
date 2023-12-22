---
title : "@Order"
excerpt : "@Order"
toc : true
toc_sticky : true
toc_label : "@Order"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2023-12-22T08:00:00-10:00:00
---

# 날짜 : 2023-12-22 14:39

# 태그 : #Spring #Annotation
---

# 내용

## Artifact
- org.springframework:spring-core

## 역할
- Bean의 우선순위를 지정

## 특징
- value가 작을수록 우선순위가 높아 앞쪽으로 정렬
- N개의 Bean중 일부만 @Order Annotation이 적용되어 있다면 나머지 Bean은 임의의 순서로 적용됨

## 사용법

```java
@Component  
@Aspect  
public class LoggingAspect {  
    @Before("execution(* com.mvcvue.controller..*.*(..))")  
    @Order(2)  
    public void beforeLogger2(JoinPoint joinPoint){  
        System.out.println("beforeLogger222");  
    }  
  
    @Before("execution(* com.mvcvue.controller..*.*(..))")  
    @Order(1)  
    public void beforeLogger1(JoinPoint joinPoint){  
        System.out.println("beforeLogger111");  
    }  
  
    @Before("execution(* com.mvcvue.controller..*.*(..))")  
    @Order(3)  
    public void beforeLogger3(JoinPoint joinPoint){  
        System.out.println("beforeLogger333");  
    }  
}
```

---

# 연결문서
