---
title : "@SuperBuilder"
excerpt : "@SuperBuilder"
toc : true
toc_sticky : true
toc_label : "@SuperBuilder"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2024-06-11T08:00:00-10:00:00
---
  
---
  
> **`@SuperBuilder`란?**  
>
>  부모 클래스의 필드를 포함한 Builder 패턴 생성을 지원하는 Lombok 어노테이션이다. 
{: .notice--info}  

  `@SuperBuilder`를 사용하면 **상속 관계에서 부모 클래스의 필드까지 포함된 빌더 객체 생성**이 가능하다.  
  주의할 점은 **부모 클래스와 자식 클래스에 모두 `@SuperBuilder` 어노테이션을 추가**해야 한다는 점이다.
  
## 사용법
  
### 1️⃣ 부모 클래스에 `@SuperBuilder` 적용
  
```java
import lombok.Getter;
import lombok.experimental.SuperBuilder;

@Getter
@SuperBuilder
public class Parent {
    private String parentField;
}
```
  
### 2️⃣ 자식 클래스에서 `@SuperBuilder` 적용
  
```java
@Getter
@SuperBuilder
public class Child extends Parent {
    private String childField;
}
```
  
### 3️⃣ 빌더 패턴으로 객체 생성
  
```java
Child child = Child.builder()
    .parentField("부모 필드 값")
    .childField("자식 필드 값")
    .build();
```
  
## 장점과 단점
  
### ✅ 장점
- 상속 관계에서 부모 필드까지 포함하여 빌더 패턴을 사용할 수 있음
- 코드를 간결하게 유지하면서 객체 생성 가능
  
### ❌ 단점
- [@Builder](../../annotation/annotation-@Builder)와 함께 사용할 수 없음  
- [Lombok](../../spring/spring-Lombok) 라이브러리에 의존적임  

---
  
# 연결문서
- [@Builder](../../annotation/annotation-@Builder)
