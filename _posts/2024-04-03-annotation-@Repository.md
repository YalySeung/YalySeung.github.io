---
title : "@Repository"
excerpt : "@Repository"
toc : true
toc_sticky : true
toc_label : "@Repository"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2024-04-03T08:00:00-10:00:00
---
  
---
  
## Artifact
  
## 역할
- persistence, DB, file 과 같은 외부 I/O 작업 처리를 위한 bean 명시
  
## 사용법
  
```java
@Repository  
public interface UserRepository extends JpaRepository<User, Integer>, CustomUserRepository{  
}
```

> **tip**
>
> @ComponentScan Annotation으로 Scan 해주어야 해당 Bean이 Conatainer에 등록됨 
{: .notice--primary}  

---
  
# 연결문서
- [@ComponentScan](../../annotation/annotation-@ComponentScan)
- [@Controller](../../annotation/annotation-@Controller)