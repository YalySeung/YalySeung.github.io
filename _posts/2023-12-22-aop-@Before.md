---
title : "@Before"
excerpt : "@Before"
toc : true
toc_sticky : true
toc_label : "@Before"
categories:
- AOP
tags:
- [Spring, Annotation, AOP]
last_modified_at: 2023-12-22T08:00:00-10:00:00
---
  
---
  
## Artifact
- org.aspectj:aspectjrt
  
## 역할
- Pointcut 명시
- JoinPoint 실행 전처리 비즈니스 로직 정의
  
## 특징
- [@Around](../../aop/aop-@Around)와 다르게 proceed 호출 없이 로직 수행 후 자동으로 target 메서드를 호출
  
## 사용법
  
```java
@Before("execution(* com.mvcvue.controller..*.*(..))")  
public void beforeLogger(JoinPoint joinPoint){  
    System.out.println("beforeLogger");  
}
```

---
  
# 연결문서
- [AOP](../../spring/spring-AOP)
- [@Aspect](../../aop/aop-@Aspect)
- [Pointcut Designator](../../spring/spring-Pointcut-Designator)
- [Advice](../../spring/spring-Advice)