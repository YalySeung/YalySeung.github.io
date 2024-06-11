---
title : "@ComponentScan"
excerpt : "@ComponentScan"
toc : true
toc_sticky : true
toc_label : "@ComponentScan"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2024-04-13T08:00:00-10:00:00
---
  
---
  
## Gradle 설정
  
## 역할
- [@Component](../../annotation/annotation-@Component) 및 [@Component](../../annotation/annotation-@Component)를 가지고있는 [@Service](../../annotation/annotation-@Service), [@Controller](../../annotation/annotation-@Controller), [@Repository](../../annotation/annotation-@Repository) Annotation이 적용된 Class를 자동으로 Scan하여 Bean으로 등록해줌
  
## 사용법

| 속성                 | 기능                               |
| ------------------ | -------------------------------- |
| basePackages       | Scan할 기본 패키지 경로 지정               |
| basePackageClasses | Scan할 클래스 명을 지정                  |
| includeFilters     | Scan 대상에 포함할 FilterType과 대상을 지정  |
| excludeFilters     | Scan 대상에서 제외할 FilterType과 대상을 지정 |
  
```java
@ComponentScan(basePackages = {"org.infinity.server"})  
public class APIConfiguration implements WebMvcConfigurer {
	...
}
```
  
```java
@ComponentScan(basePackageClasses = {UserRepository.class, UserController.class})  
public class APIConfiguration implements WebMvcConfigurer {
	...
}
```
  
```java
@ComponentScan(useDefaultFilters = false, 
        includeFilters = {@Filter(type = FilterType.ANNOTATION, value = {Controller.class, RestController.class})})  
public class MyWebMvcConfiguration extends WebMvcConfigurerAdapter {
	...
}
```
  
```java
@ComponentScan(basePackages = {"com.mobileleader.rpa"},  
        excludeFilters = {  
        @Filter(type = FilterType.ANNOTATION,  
                value = {EnableWebMvc.class, Controller.class, RestController.class,  
                        EnableSwagger2.class, EnableTransactionManagement.class}),  
        @Filter(type = FilterType.ASSIGNABLE_TYPE, value = QuerydslConfiguration.class)})  
...
public class RpaViewConfiguration extends AnnotationConfigApplicationContext {
}
```

---
  
# 연결문서