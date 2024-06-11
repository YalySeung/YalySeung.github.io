---
title : "@Aspect"
excerpt : "@Aspect"
toc : true
toc_sticky : true
toc_label : "@Aspect"
categories:
- AOP
tags:
- [Spring, Annotation, AOP]
last_modified_at: 2023-12-14T08:00:00-10:00:00
---
  
---
  
## Artifact
- org.aspectj:aspectjrt
  
## 설정
  
### build.gradle
  
```groovy
implementation 'org.springframework:spring-aop:3.2.3.RELEASE'  
implementation 'org.aspectj:aspectjrt:1.6.10'  
implementation 'org.aspectj:aspectjweaver:1.9.19'
```
  
### WebMvcConfigurer
  
```java
@EnableWebMvc  
@ComponentScan(basePackages = "com.mvcvue")  
@EnableAspectJAutoProxy  
public class VueMvcConfigurer implements WebMvcConfigurer {
...
}
```

> **caution**
>
> @EnableAspectJAutoProxy Annotation은 Spring Bean이 초기되 된 이후 시점에 적용되어야 한다. 
{: .notice--danger}  
  
## 역할
- Advisor를 만들기 위한 Annotation

> **caution**
>
> @Aspect Annotation Component 스캔 기능이 없으므로 반드시 Bean으로 등록해줘야한다.
> **@Bean @Component @Import** 
{: .notice--danger}  
  
## 사용법
  
### @Aspect
- @Aspect Annotation 적용
- Class에 적용해야한다.
- [Advice 선언](../../spring/spring-Advice) [Pointcut 적용](../../spring/spring-Pointcut-Designator)
  
```java
@Component
@Aspect
public class LoggingAspect {
    @Around("* com.test..*.*(..)")
    public void beforeLogger(JoinPoint joinPoint){
        System.out.println("---------Before---------");
    }
}
```
  
### @EnableAspectJAutoProxy
- Configure에 @EnableAspectJAutoProxy Annotation 적용
  
```java
@EnableWebMvc  
@ComponentScan(basePackages = "com.mvcvue")
@EnableAspectJAutoProxy()  
public class VueMvcConfigurer implements WebMvcConfigurer {  
    ...
}
```

---
  
# 연결문서
- [WebMvcConfigurer](../../spring/spring-WebMvcConfigurer)
- [AOP](../../spring/spring-AOP)
- [Pointcut Designator](../../spring/spring-Pointcut-Designator)
- [Advice](../../spring/spring-Advice)