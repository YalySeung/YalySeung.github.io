---
title : "@EnableJpaRepositories"
excerpt : "@EnableJpaRepositories"
toc : true
toc_sticky : true
toc_label : "@EnableJpaRepositories"
categories:
- JPA
tags:
- [Spring, Annotation]
last_modified_at: 2024-04-15T08:00:00-10:00:00
---
  
---
  
## Artifact
  
## 역할
- JPA Repository Bean을 활성화
  
## 사용법
  
```java
@Configuration
@EnableJpaRepositories(basePackages = "org.infinity.server.repository")  
@EnableJpaAuditing  
@EnableTransactionManagement  
public class JpaConfiguration {
	...
}
```

> **tip**
>
> basePackages 를 설정하지 않으면 현재 클래스가 속한 패키지를 기준으로 JPA Repository를 Scan함 
{: .notice--primary}  

---
  
# 연결문서
- [JPA](../../jpa/jpa-JPA)
- [@Repository](../../annotation/annotation-@Repository)