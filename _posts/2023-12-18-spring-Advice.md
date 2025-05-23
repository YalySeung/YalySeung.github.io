---
title : "Advice"
excerpt : "Advice"
toc : true
toc_sticky : true
toc_label : "Advice"
categories:
- Spring
tags:
- [Spring, AOP]
last_modified_at: 2023-12-18T08:00:00-10:00:00
---
  
---
  
## 정의
> **Advice란?**  
>
> 실질적으로 프록시에서 수행하게 되는 로직을 명세 
{: .notice--info}  
  
## 특징
  
## 종류
  
| Advice종류        | 설명                                    |
| --------------- | :------------------------------------ |
| @Around         | 메서드 호출 전후작업 조인포인트 실행여부 반환값 예외 등 설정 가능 |
| @Before         | JoinPoint 이전에 실행                      |
| @AfterReturning | JoinPoint 정상 완료 후 실행                  |
| @AfterThrowing  | 메서드에서 예외가 발생할 경우 실행                   |
| @After]]        | JoinPoint 정상, 예외 발생과 무관하게 실행          |
  
### Annotation 동작 순서
  
![image](../../assets/images/AdviceAnnotationOrder.png)

> **tip**
>
> 같은 Advice가 한 JoinPoint에 적용되어 있을 경우 임의의 순서로 동작하는데, 이때 [@Order](../../jpa/jpa-@Order) Annotation을 적용하여 순서를 지정할 수 있다. 
{: .notice--info}  
  
## Example
  
```java
//LoggingAspect
@Component  
@Aspect  
public class LoggingAspect {  
    @Around("execution(* com.mvcvue.controller..*.*(..))")  
    public Object aroundLogger(ProceedingJoinPoint joinPoint) throws Throwable{  
        System.out.println("aroundLogger");  
        return joinPoint.proceed();  
    }  
  
    @Before("execution(* com.mvcvue.controller..*.*(..))")  
    public void beforeLogger(JoinPoint joinPoint){  
        System.out.println("beforeLogger");  
    }  
  
    @AfterReturning("execution(* com.mvcvue.controller..*.*(..))")  
    public void afterReturningLogger(JoinPoint joinPoint){  
        System.out.println("afterReturningLogger");  
    }  
  
    @AfterThrowing("execution(* com.mvcvue.controller..*.*(..))")  
    public void afterThrowingLogger(JoinPoint joinPoint){  
        System.out.println("afterThrowingLogger");  
    }  
  
    @After("execution(* com.mvcvue.controller..*.*(..))")  
    public void afterLogger(JoinPoint joinPoint){  
        System.out.println("afterLogger");  
    }  
}
```
  
```java
//HelloController
@Controller  
@RequestMapping("/api/hello")  
public class HelloController {  
    @GetMapping  
    public ResponseEntity<String> hello(){  
        System.out.println("Hello Contoller 로직 수행!");  
        return ResponseEntity.ok("hello");  
    }  
  
    @GetMapping("/exception")  
    public void exception() throws FileNotFoundException {  
        throw  new FileNotFoundException();  
    }  
}
```
  
### API 호출 테스트 결과
- http://localhost:8080/api/hello
  
![image](../../assets/images/PostManCallHelloAPI.png)
  
![image](../../assets/images/CallHelloAPIResult.png)

- http://localhost:8080/api/hello/exception
  
![image](../../assets/images/PostManCallExceptionResult.png)
  
![image](../../assets/images/CallExceptionAPIResult.png)

---
  
# 연결문서
- [Pointcut Designator](../../spring/spring-Pointcut-Designator)
- [AOP](../../spring/spring-AOP)
- [@Order](../../jpa/jpa-@Order)