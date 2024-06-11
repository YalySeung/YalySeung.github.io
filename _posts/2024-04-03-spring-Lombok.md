---
title : "Lombok"
excerpt : "Lombok"
toc : true
toc_sticky : true
toc_label : "Lombok"
categories:
- Spring
tags:
- [Spring, Lombok]
last_modified_at: 2024-04-03T08:00:00-10:00:00
---
  
---
  
## 정의
> **Lombok 이란?**  
>
> Java 라이브러리 중 하나로 반복되는 코드를 Annotation을 사용하여 자동으로 생성해주는 라이브러리 
{: .notice--info}  
  
## 장점
- Annotation 기반의 코드 자동 생성으로 생산성 향상
- 코드 가독성 향상
- 유지보수 편의성 향상
  
## Lombok Annotation

| Annotation               | 대상        | 기능                                                                          |
| ------------------------ | --------- | --------------------------------------------------------------------------- |
| @Getter                  | Class, 변수 | Getter 메서드 생성                                                               |
| @Setter                  | Class, 변수 | Setter 메서드 생성                                                               |
| @ToString                | Class     | Class 필드를 기반으로 toString 메서드 생성                                              |
| @NoArgsConstructor       | Class     | 기본 생성자를 생성                                                                  |
| @AllArgsConstructor      | Class     | Class 필드를 파라미터로 받는 생성자를 생성                                                  |
| @RequiredArgsConstructor | Class     | 특정 필드만을 파라미터로 받는 생성자를 생성. 생성자의 파라미터로 추가할 변수에 @NotNull 또는 final을 선언하여 의존성 주입 |
| @EqualsAndHashCode       | Class     | equals 와 hashCode 함수 생성. callSuper(부모의 필드도 비교할지 여부)                         |
| [@Data](../../annotation/annotation-@Data)                | Class     | Getter 메서드, Setter 메서드, RequiredArgsConstructor, toString, equals 모두 생성     |
| @Builder                 | Class     | 해당 Class에 Builder 패턴 적용                                                     |
  
## 프로젝트 설정
- IDE에서 Annotation Processor 옵션을 활성화 해야 한다. [Intellij](../../ide/ide-Intellij#annotationprocessor)
  
### build.gradle
  
```groovy
dependencies {  
    ...
    //lombok  
    compileOnly 'org.projectlombok:lombok:1.18.22'  
    annotationProcessor 'org.projectlombok:lombok:1.18.22'  
	...
}
```
  
### Example
  
```java
@Data  
public class User {  
    Integer userSeq;  
    String id;  
    LocalDate registTime;  
    LocalDate lastLoginTime;  
}
```

---
  
# 연결문서
- [@Data](../../annotation/annotation-@Data)
- [AnnotationProcessor](../../spring/spring-AnnotationProcessor)
- [Intellij](../../ide/ide-Intellij#annotationprocessor)