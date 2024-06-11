---
title : "@Autowired"
excerpt : "@Autowired"
toc : true
toc_sticky : true
toc_label : "@Autowired"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2024-01-05T08:00:00-10:00:00
---
  
---
  
## Artifact
- spring-beans
  
## 역할
- 필요한 의존 객체의 타입에 해당하는 bean을 찾아 주입
- 동일한 Bean이 2개 이상이면 오류를 발생
- 두 개 이상의 클래스로 하나의 인터페이스를 구현할 경우 [@Qualifier](../../annotation/annotation-@Qualifier) Annotation으로 특정 Bean을 가져오겠다는 명시 필요
  
## 적용 대상
- Constructor
- Setter
- Field
  
## DI 방법
  
### Constructor Injection
- 가장 권장되는 방식의 DI 방식
- 생성자에서 의존성을 주입받고자 하는 field를 나열하는 방법
- 매개변수가 bean으로 등록되어있지 않다면 생성자에서 에러 발생
  
```java
@Service
public class MyService {
	private MyDao myRepository;
	
	@Autowired 
	public MyService(MyRepository myRepository) { 
		this.myRepository = myRepository; 
	}
}
```
  
### Setter Injection
- setter 메소드에 @Autowired annotation을 선언
  
```java
@Service
public class MyService {
	private MyDao myRepository;
	
	@Autowired
	public setMyRepository(MyRepository myRepository) { 
		this.myRepository = myRepository; 
	}
}
```
  
### Field Injection
- 단일 책임의 원칙 위반, 객체의 오염 가능성이 있다는 단점
- 사용하기 쉽다는 장점
- field에 @Autowired annotation을 선언
  
```java
@Autowired  
private ConfigValueWebService configValueWebService;
```

---
  
# 연결문서
- [@Qualifier](../../annotation/annotation-@Qualifier)