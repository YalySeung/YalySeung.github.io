---
title : "@Convert"
excerpt : "@Convert"
toc : true
toc_sticky : true
toc_label : "@Convert"
categories:
- JPA
tags:
- [Spring, Annotation, JPA]
last_modified_at: 2024-04-25T08:00:00-10:00:00
---
  
---
  
## Artifact
- javax.persistence
  
## 역할
- [@Entity](../../jpa/jpa-@Entity)의 데이터를 변환해서 데이터베이스에 저장 할 수 있음
  
## 사용법
  
### Global 설정
  
```java
@Converter(autoApply = true)  
public class LocalDateAttributeConverter implements AttributeConverter<LocalDate, LocalDateTime> {  
    @Override  
    public LocalDateTime convertToDatabaseColumn(LocalDate localDate) {  
        return localDate != null ? localDate.atStartOfDay() : null;  
    }  
  
    @Override  
    public LocalDate convertToEntityAttribute(LocalDateTime localDateTime) {  
        return localDateTime != null ? localDateTime.toLocalDate() : null;  
    }  
}
```

| 속성        | 기능                                            |
| --------- | --------------------------------------------- |
| autoApply | 대상 타입에 대해 @Convert 설정 없이 자동으로 적용할지 여부(글로벌 설정) |
  
### 필드 설정
  
```java
@Entity  
@Data  
@Table(name = "user")  
public class User {  

    @GeneratedValue(strategy = GenerationType.AUTO)  
    @Column(name = "user_seq", length = 20, nullable = false)  
    Integer userSeq;  
	
	...
  
    @Column(name = "regist_time", nullable = false)  
    @Convert(converter = LocalDateAttributeConverter.class)  
    LocalDate registTime;  
  
    @Column(name = "last_login_time")  
    @Convert(converter = LocalDateAttributeConverter.class)  
    LocalDate lastLoginTime;  
}

```
  
### class 설정
  
```java
@Entity  
@Data  
@Table(name = "user")
@Converter(converter = LocalDateAttributeConverter.class, attributeName = "registTime") 
public class User {  
	...
}
```

---
  
# 연결문서
- [@Entity](../../jpa/jpa-@Entity)