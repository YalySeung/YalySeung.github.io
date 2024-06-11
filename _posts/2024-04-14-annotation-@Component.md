---
title : "@Component"
excerpt : "@Component"
toc : true
toc_sticky : true
toc_label : "@Component"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2024-04-14T08:00:00-10:00:00
---
  
---
  
## Artifact
- org.springframework.stereotype
  
## 역할
- Component로 선언된 Class는 Spring Bean 으로 등록되고 자동으로 빈 탐색의 대상의 됨
  
## 사용법
  
```java
@Component  
public class UserSupport {
	...
}
```

> **tip**
>
> @ComponentScan으로 Container에 등록해줘야 App 에서 사용이 가능하다 
{: .notice--primary}  

---
  
# 연결문서
- [@ComponentScan](../../annotation/annotation-@ComponentScan)
- [@Controller](../../annotation/annotation-@Controller)
- [@Service](../../annotation/annotation-@Service)
- [@Repository](../../annotation/annotation-@Repository)