---
title : "@AfterReturning"
excerpt : "@AfterReturning"
toc : true
toc_sticky : true
toc_label : "@AfterReturning"
categories:
- AOP
tags:
- [Spring, Annotation, AOP]
last_modified_at: 2023-12-22T08:00:00-10:00:00
---

# 날짜 : 2023-12-22 14:18

# 태그 : #Spring #Annotation #AOP
---

# 내용

## Artifact
- org.aspectj:aspectjrt

## 역할
- Pointcut 명시
- JoinPoint 정상 처리 후 비즈니스 로직 정의 (Exception 발생시 미동작)

## 특징
- [@Around](../../aop/aop-@Around)와 다르게 proceed 호출 없이 로직 수행 후 자동으로 target 메서드를 호출

## 사용법

```java
@AfterReturning("execution(* com.mvcvue.controller..*.*(..))")  
public void afterReturningLogger(JoinPoint joinPoint){  
    System.out.println("afterReturningLogger");  
}
```

---

# 연결문서
- [AOP](../../spring/spring-AOP)
- [@Aspect](../../aop/aop-@Aspect)
- [Pointcut Designator](../../spring/spring-Pointcut-Designator)
- [Advice](../../spring/spring-Advice)