---
title : "@NoArgsConstructor"
excerpt : "@NoArgsConstructor"
toc : true
toc_sticky : true
toc_label : "@NoArgsConstructor"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2024-04-03T08:00:00-10:00:00
---
  
---
  
 @NoArgsConstructor 는 [Lombok](../../spring/spring-Lombok)에서 제공하는 Annotation 중 하나로 파라미터가 없는 생성자를 만들어주는 역할을 한다.

 [Lombok](../../spring/spring-Lombok)을 사용하려면 gradle 에서 의존성을 추가해준다.
  
```groovy
dependencies {
	...
	compileOnly 'org.projectlombok:lombok:1.18.22'

	annotationProcessor 'org.projectlombok:lombok:1.18.22'
	...
}
```

 의존성을 추가했다면, Class에 Annotation을 추가하자.
  
```java
@NoArgsConstructor
public class User{
	String name;
	Integer age;
}
```

 기본 생성자가 추가 된 것을 확인 할 수 있다.
 
---
  
# 연결문서
- [Lombok](../../spring/spring-Lombok)