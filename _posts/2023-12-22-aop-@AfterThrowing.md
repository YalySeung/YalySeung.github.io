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

# 날짜 : 2023-12-22 14:20

# 태그 : #Spring #Annotation #AOP
---

# 내용

## Artifact
- org.aspectj:aspectjrt

## 역할
- Pointcut 명시
- JoinPoint 에서 Exception 발생 후 비즈니스 로직 정의

## 특징
- [@Around](../../aop/AOP-@Around)와 다르게 proceed 호출 없이 로직 수행 후 자동으로 target 메서드를 호출

## 사용법

```java
@AfterThrowing("execution(* com.mvcvue.controller..*.*(..))")  
public void afterThrowingLogger(JoinPoint joinPoint){  
    System.out.println("afterThrowingLogger");  
}
```

---

# 연결문서
- [AOP](../../spring/Spring-AOP)
- [@Aspect](../../aop/AOP-@Aspect)
- [Pointcut Designator](../../spring/Spring-Pointcut-Designator)
- [Advice](../../spring/Spring-Advice)