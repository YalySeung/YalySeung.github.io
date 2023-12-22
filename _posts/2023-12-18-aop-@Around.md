---
title : "@Around"
excerpt : "@Around"
toc : true
toc_sticky : true
toc_label : "@Around"
categories:
- AOP
tags:
- [Spring, Annotation, AOP]
last_modified_at: 2023-12-18T08:00:00-10:00:00
---

# 날짜 : 2023-12-18 13:56

# 태그 : #Spring #Annotation #AOP
---

# 내용

## Artifact
- org.aspectj:aspectjrt

## 역할
- Pointcut 명시

## 특징
- proceed를 반드시 명시적으로 적어야한다.
- 입력, 반환값 자체를 다른 객체로 조작 가능

## 파라미터

### ProceedingJoinPoint

| 주요 기능      | 설명                             |
| -------------- |:-------------------------------- |
| getArgs()      | 메서드 인수 반환                 |
| getThis()      | 프록시 객체 반환                 |
| getTarget()    | 대상 객체 반환                   |
| getSignature() | 조언되는 메서드에 대한 설명      |
| toString()     | 조언되는 방법에 대한 유용한 설명 |
| proceed()      | 다음 Advice, Target method 호출               |

## 사용법
- [@Aspect](../../aop/AOP-@Aspect)가 적용된 Class 하위 메서드에 Around Annotation을 사용

```java
@Around("execution(* com.mvcvue.controller..*.*(..))")  
public Object aroundLogger(ProceedingJoinPoint joinPoint, Object obj) throws Throwable{  
    System.out.println("Around Pointcut");  
    return joinPoint.proceed();  
}
```

---

# 연결문서
-  [AOP](../../spring/Spring-AOP)
- [@Aspect](../../aop/AOP-@Aspect)
- [Pointcut Designator](../../spring/Spring-Pointcut-Designator)
- [Advice](../../spring/Spring-Advice)