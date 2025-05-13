---
title : "AOPAnnotations"
excerpt : "AOPAnnotations"
toc : true
toc_sticky : true
toc_label : "AOPAnnotations"
categories:
- AOP
tags:
- [Spring, AOP, Annotation]
last_modified_at: 2025-03-24T08:00:00-10:00:00
---
  
---
  
> **Spring AOP (Aspect-Oriented Programming) 주요 어노테이션 정리**  
>
> Spring AOP는 비즈니스 로직과 공통 기능(로깅, 보안 등)을 분리하여 코드 중복을 줄이고 관리 효율성을 높이는 프레임워크이다. 
{: .notice--info}  

---
  
## 📌 @Aspect
- AOP의 중심 Annotation으로 Advisor 정의를 위한 클래스에 적용.
- 별도의 컴포넌트 스캔 기능이 없기 때문에 Bean 등록 필요 (`@Bean`, `@Component`, `@Import` 사용).
  
### 설정 예시
  
```java
@Component
@Aspect
public class LoggingAspect {
    @Before("execution(* com.example..*.*(..))")
    public void logBefore(JoinPoint joinPoint){
        System.out.println("Before method: " + joinPoint.getSignature().getName());
    }
}
```

---
  
## 📌 @Before
- 대상 메서드 실행 전 처리할 로직 정의.
- 대상 메서드는 자동 호출됨.
  
### 예시
  
```java
@Before("execution(* com.example.controller..*.*(..))")  
public void beforeAdvice(JoinPoint joinPoint){  
    System.out.println("메서드 실행 전 호출됨: " + joinPoint.getSignature().getName());  
}
```

---
  
## 📌 @After
- 대상 메서드 실행 이후, 예외 발생 여부와 상관없이 항상 호출.
  
### 예시
  
```java
@After("execution(* com.example.controller..*.*(..))")  
public void afterAdvice(JoinPoint joinPoint){  
    System.out.println("메서드 실행 후 항상 호출됨: " + joinPoint.getSignature().getName());  
}
```

---
  
## 📌 @AfterReturning
- 대상 메서드가 정상적으로 실행 완료 후 호출.
- 예외 발생 시 실행되지 않음.
  
### 예시
  
```java
@AfterReturning("execution(* com.example.controller..*.*(..))")  
public void afterReturningAdvice(JoinPoint joinPoint){  
    System.out.println("정상 실행 후 호출됨: " + joinPoint.getSignature().getName());  
}
```

---
  
## 📌 @AfterThrowing
- 대상 메서드 실행 중 예외 발생 시에만 호출.
  
### 예시
  
```java
@AfterThrowing("execution(* com.example.controller..*.*(..))")  
public void afterThrowingAdvice(JoinPoint joinPoint){  
    System.out.println("예외 발생 후 호출됨: " + joinPoint.getSignature().getName());  
}
```

---
  
## 📌 @Around
- 대상 메서드 실행 전후에 모두 관여할 수 있는 가장 강력한 Annotation.
- 메서드 실행을 직접 제어하며, 반드시 `proceed()`를 호출하여 대상 메서드를 실행해야 함.
  
### 예시
  
```java
@Around("execution(* com.example.controller..*.*(..))")  
public Object aroundAdvice(ProceedingJoinPoint joinPoint) throws Throwable{  
    System.out.println("메서드 실행 전 호출됨");
    Object result = joinPoint.proceed();
    System.out.println("메서드 실행 후 호출됨");
    return result;
}
```

| 메서드명 | 설명 |
|---------|------|
| getArgs() | 메서드 인수 반환 |
| getThis() | 프록시 객체 반환 |
| getTarget() | 대상 객체 반환 |
| proceed() | 대상 메서드 직접 호출 |

---
  
## 📌 Annotation 비교표

| Annotation       | 실행 시점             | 메서드 호출 방법 |
|------------------|----------------------|------------------|
| `@Before`        | 메서드 실행 전        | 자동             |
| `@After`         | 메서드 실행 후 (항상) | 자동             |
| `@AfterReturning`| 정상 실행 후          | 자동             |
| `@AfterThrowing` | 예외 발생 시          | 자동             |
| `@Around`        | 메서드 실행 전후      | 수동 (`proceed()`) |

---
  
## 📌 설정 및 의존성 추가 (Gradle)
  
```groovy
implementation 'org.springframework.boot:spring-boot-starter-aop'
implementation 'org.aspectj:aspectjrt'
implementation 'org.aspectj:aspectjweaver'
```
  
### AOP 활성화 예시
  
```java
@Configuration
@EnableAspectJAutoProxy
public class AopConfig {}
```

---
  
## 📌 장점과 단점
  
### ✅ 장점
- **중복 코드 최소화**
- **로직 모듈화 및 유지보수 용이**
- **횡단 관심사의 명확한 분리**
  
### ❌ 단점
- **실행 흐름 복잡성 증가 가능성**
- **성능 저하 가능성 존재**

---
  
# 연결 문서
- [AOP](../../spring/spring-AOP)
- [Pointcut Designator](../../spring/spring-Pointcut-Designator)
- [Advice](../../spring/spring-Advice)
