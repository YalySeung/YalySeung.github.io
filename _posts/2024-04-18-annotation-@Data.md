---
title : "@Data"
excerpt : "@Data"
toc : true
toc_sticky : true
toc_label : "@Data"
categories:
- Annotation
tags:
- [Spring, Annotation, Lombok]
last_modified_at: 2024-04-18T08:00:00-10:00:00
---
  
---
  
## Artifact
- lombok
  
## 역할
- @Getter, @Setter, @ToString, @EqualsAndHashCode, @RequiredArgsConstructor 등이 [Boiler Plate](../../cleancode/cleancode-Boiler-Plate)를 생성
  
## 사용법
  
```java
@Entity
@Data
@Table(name = "MY_USER")  
public class User {

}
```

---
  
# 연결문서
- [Boiler Plate](../../cleancode/cleancode-Boiler-Plate)
- [Lombok](../../spring/spring-Lombok)