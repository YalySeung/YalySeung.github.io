---
title : "Pointcut Designator"
excerpt : "Pointcut Designator"
toc : true
toc_sticky : true
toc_label : "Pointcut Designator"
categories:
- Spring
tags:
- [Spring]
last_modified_at: 2023-12-18T08:00:00-10:00:00
---

# 날짜 : 2023-12-18 15:04

# 태그 : #Spring
---

# 내용

## 정의
> Pointcut 지시자란?
> 어떤 메서드가 Aspect에 의해 가로채질 것인지 패턴으로 지정

## 메서드 선택

### execution
- 가장 많이 사용되는 지시자
- **execution(<접근제한자> <반환타입> <패키지>.<패키지>.<클래스>.<메소드>(<인자>))**
- <접근제한자> <반환타입> <패키지경로>.\<ClassName>.<메서드명>(<매개변수>)
- 여기서 **..**은 임의의 개수의 패키지 레벨이나 임의의 개수의 매개변수, **\*** 는 임의의 문자열을 의미
- <접근제한자> 항목은 생략이 가능하며 모든 접근 제한자를 지시한다.

#### example

```java
// 메서드 직접 지정
execution(public String com.mvcvue.controller.api.hello.HelloController.hello())

// 반환타입 모두 포함, 함수명 패턴 적용
execution(public * com.mvcvue.controller.api.hello.HelloController.*ell*())

// 반환타입 모두 포함, 패키지 하위 모든 클래스, 함수명 패턴 적용, 파라미터 모두 포함
execution(public * com.mvcvue.controller.api.hello.*.*ell*(..))

// 모든 접근제한자, controller 하위 패키지의 모든 클래스의 모든 메서드 포함, 파라미터 모두 포함
execution(* com.mvcvue.controller..*.*(..))
```

### within
- [execution](#execution)에서 패키지와 클래스 부분만 사용

#### example

```java
//com.mvcvue.controller 하위 모든 패키지의 모든 클래스
within(com.mvcvue.controller..*)
```

### @target
- 인스턴스의 모든 메서드를 Joinpoint로 적용
- 즉 부모타입의 메서드까지 포함

#### example

```java
@target(org.springframework.stereotype.Controller)
```

### @within
- 인스턴스의 모든 메서드를 Joinpoint로 적용
- 해당 타입 내에 있는 메서드만 Joinpoint로 적용

#### example

```java
@within(org.springframework.stereotype.Controller)
```

## 매개변수 전달

### @annotation
- Method의 Annotation 검색

#### example

```java
@Around("@annotation(org.springframework.web.bind.annotation.GetMapping)")
```

### args
- 매칭되는 메서드에서 매개변수만 얻어올 때 사용

#### example

```java
@Around("args(arg)")  
public Object aroundArgLogger(ProceedingJoinPoint joinPoint, String arg) throws Throwable{  
    System.out.println("arg : " + arg);  
    return joinPoint.proceed();  
}
```

### this
- 매칭되는 메서드에서 프록시 객체를 가져올때, 사용

#### example

```java
@Around("execution(* com.mvcvue.controller..*.*(..)) && this(obj)")  
public Object aroundLogger(ProceedingJoinPoint joinPoint, Object obj) throws Throwable{  
    System.out.println("obj : " + obj);  
    return joinPoint.proceed();  
}
```

### target
- 매칭되는 메서드에서 실제 대상 객체를 가져올 때, 사용

#### example

```java
@Around("execution(* com.mvcvue.controller..*.*(..)) && this(obj) && target(targetObj)")  
public Object aroundLogger(ProceedingJoinPoint joinPoint, Object obj, Object targetObj) throws Throwable{  
    System.out.println("obj : " + obj);  
    System.out.println("targetObj : " + targetObj);  
    return joinPoint.proceed();  
}
```

---

# 연결문서
- [AOP](../../spring/Spring-AOP)
- [@Aspect](../../aop/AOP-@Aspect)
- [Advice](../../spring/Spring-Advice)