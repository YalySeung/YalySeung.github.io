---
title : "@Table"
excerpt : "@Table"
toc : true
toc_sticky : true
toc_label : "@Table"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2024-04-03T08:00:00-10:00:00
---
  
---
  
## Artifact
- javax.persistence
  
## 역할
- [@Entity](../../jpa/jpa-@Entity) 와 매핑할 테이블을 지정
- 생략할 경우 Entity 이름을 테이블명으로 사용
  
## 사용법
  
```java
@Entity  
@Data  
@Table(name = "user")  
public class User {  
	...
}
```

---
  
# 연결문서
- [@Entity](../../jpa/jpa-@Entity)