---
title : "@Builder"
excerpt : "@Builder"
toc : true
toc_sticky : true
toc_label : "@Builder"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2024-06-11T08:00:00-10:00:00
---
  
---
  
 **@Builder** Annotation은 Lombok 라이브러리에서 제공하는 기능으로 **빌더 패턴을 자동으로 생성**해준다. 
 
 빌더 패턴은 객체의 생성 과정을 보다 유연하게 다루기 위한 디자인 패턴으로 많은 매개변수를 가진 생성자를 사용할 때, 유용하다.
  
## 사용법
 @Builder Annotation을 클래스에 적용하면, 해당 클래스에 빌더 클래스를 자동으로 생성해준다.
  
```java
import lombok.Builder; 
import lombok.Getter; 

@Getter @Builder 
public class Person { 
	private String name; 
	private int age; 
	private String address; 
}
```

 이렇게 Class를 선언했다면,
  
```java
Person person = Person.builder()
   .name("John Doe")
   .age(30)
   .address("123 Elm Street")
   .build();
```

 위와 같이 간단하게 Person 객체를 생성할 수 있다.

> **caution**
>
> 위와 같이 객체를 생성할 때, 각 변수에 값이 할당되는 방식은 setter 메서드를 통한 것이 아니다! 그렇기 때문에 외부에서 다른 타입의 변수를 할당하고 Builder에서 변경하려면, Custom Builder 를 선언해야 한다. 
{: .notice--danger}  

---
  
# 연결문서
- [Lombok](../../spring/spring-Lombok)
- [@SuperBuilder](../../annotation/annotation-@SuperBuilder)