---
title : "@Embeddable"
excerpt : "@Embeddable"
toc : true
toc_sticky : true
toc_label : "@Embeddable"
categories:
- JPA
tags:
- [Spring, Annotation, Querydsl]
last_modified_at: 2024-04-03T08:00:00-10:00:00
---
  
---
  
## Artifact
  
## 역할
- 객체 지향 모델에 있는 속성을 데이터베이스 테이블의 컬럼으로 매핑
- 주로 두개 이상의 Entity가 공유하는 속성이 있는 경우에 사용
  
## 사용법
- @Embedded Annotation 이 적용된 클래스 생성
- @Embedded Annotation을 사용하여 해당 클래스의 객체를 Entity 클래스에 매핑
  
```java
@Embeddable
public class Address {
    private String street;
    private String city;
    private String state;
    private String zipCode;
}

@Entity
public class Person {
    @Id
    private Long id;
    
    private String name;
    
    @Embedded
    private Address address;
}
```

---
  
# 연결문서
- [JPA](../../jpa/jpa-JPA)
- [@Entity](../../jpa/jpa-@Entity)