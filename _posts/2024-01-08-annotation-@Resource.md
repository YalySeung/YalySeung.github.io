---
title : "@Resource"
excerpt : "@Resource"
toc : true
toc_sticky : true
toc_label : "@Resource"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2024-01-08T08:00:00-10:00:00
---
  
---
  
## Artifact
- javax.annotation-api
  
## 역할
- 객체의 id가 일치하는 객체를 자동으로 주입
  
## 사용법
- 반드시 기본 생성자가 정의되어 있어야함
  
### Field Injection
  
```java
import javax.annotation.Resource; 
public class UserRegisterService { 
	@Resource 
	private UserDao userDao;
	
	public UserRegisterServiceUseResource() { 
		...
	} 
}
```
  
### Setter Injection
  
```java
import javax.annotation.Resource; 
public class UserRegisterService { 
	private UserDao userDao;
	
	public UserRegisterServiceUseResource() { 
		...
	} 
	
	@Resource 
	public UserRegisterServiceUseResource(UserDao userDao) { 
		this.userDao = userDao;
	}
}
```

---
  
# 연결문서
- [@Autowired](../../annotation/annotation-@Autowired)