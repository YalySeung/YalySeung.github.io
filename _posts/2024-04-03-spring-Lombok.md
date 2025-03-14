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
  
 이 글에서는 Spring 개발에서 빼놓을 수 없는 Lombok 라이브러리에 대해서 알아보겠다.

> **Lombok 이란?**  
>
> Java 라이브러리 중 하나로 반복되는 코드를 Annotation을 사용하여 자동으로 생성해주는 라이브러리이다. 
{: .notice--info}  

 Lombok을 사용함으로써 얻을 수 있는 가장 큰 이점은 [Boiler Plate](../../cleancode/cleancode-Boiler-Plate) 를 줄여 **가독성**을 높이고 **유지보수 편의성을 향상**시킬 수 있으며, 간단한 Annotation만으로 코드 작성을 줄일 수 있다는 점이다.
  
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
| [@SuperBuilder](../../annotation/annotation-@SuperBuilder)        | Class     | @Builder + 상속 관계까지 반영                                                       |
  
## 프로젝트 설정
 Lombok을 사용하기 위해서 IDE의 Annotation Processor 옵션을 활성화 해야 한다. [IntelliJ Annotation Processor 활성화](../../ide/ide-Intellij#annotationprocessor)

 IDE 설정이 완료됐다면, Gradle 에 의존성을 설정해준다.
  
```groovy
dependencies {  
    ...
    //lombok  
    compileOnly 'org.projectlombok:lombok:1.18.22'  
    annotationProcessor 'org.projectlombok:lombok:1.18.22'  
	...
}
```

 아래는 @Data Annotation을 적용하여 getter, getter, equals, hashCode를 정의한 모습니다. 보다시피 소스코드가 굉장히 간소화 된 것을 볼 수 있다.
  
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