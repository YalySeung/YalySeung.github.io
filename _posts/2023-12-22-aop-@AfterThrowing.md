---
title : "@AfterThrowing"
excerpt : "@AfterThrowing"
toc : true
toc_sticky : true
toc_label : "@AfterThrowing"
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
- JoinPoint 에서 Exception 발생 후 비즈니스 로직 정의
  
## 특징
- [@Around](../../aop/aop-@Around)와 다르게 proceed 호출 없이 로직 수행 후 자동으로 target 메서드를 호출
  
## 사용법
  
```java
@AfterThrowing("execution(* com.mvcvue.controller..*.*(..))")  
public void afterThrowingLogger(JoinPoint joinPoint){  
    System.out.println("afterThrowingLogger");  
}
```

---
  
# 연결문서
- [AOP](../../spring/spring-AOP)
- [@Aspect](../../aop/aop-@Aspect)
- [Pointcut Designator](../../spring/spring-Pointcut-Designator)
- [Advice](../../spring/spring-Advice)