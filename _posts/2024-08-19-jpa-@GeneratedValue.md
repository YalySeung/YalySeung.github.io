---
title : "@GeneratedValue"
excerpt : "@GeneratedValue"
toc : true
toc_sticky : true
toc_label : "@GeneratedValue"
categories:
- JPA
tags:
- [Spring, Annotation, JPA]
last_modified_at: 2024-08-19T08:00:00-10:00:00
---
  
---
  
 @GenratedValue Annotation은 JPA에서 [@Entity](../../jpa/jpa-@Entity)의 **primary key가 자동으로 생성**되도록 하는 데 사용되는 Annotation이다.
  
## 주요 속성

| 속성명       | 기능                             |
| --------- | ------------------------------ |
| strategy  | primary key 생성 전략을 정의          |
| generator | 특정 시퀀스나 테이블을 사용하고자 할 때, 이름을 지정 |

 strategy 속성은 4가지 값을 가질 수 있는데

 **GenerationType.AUTO** 는 primary key 생성 전략을 **JPA 구현체에 맡긴다**. 대부분의 경우 JPA 구현체는 데이터베이스의 dialect 에 따라 적절한 전략을 자동으로 선택한다.

 **GenerationType.IDENTITY** 는 primary key 생성을 **데이터베이스에 위임**한다. MySQL, postgreSQL 등의 데이터 베이스에서 AUTO_INCREMENT와 같은 방식으로 기본키가 생성된다.

 **GenerationType.SEQUENCE** 는 **데이터베이스의 시퀀스**를 사용하여 primary key를 생성한다.

 **GenerationType.TABLE** 은 **별도의 테이블을 만들어** key 값을 관리하는 전략이다.
  
```java
@Entity  
@Builder  
@Data  
@NoArgsConstructor @AllArgsConstructor  
@Table(name = "user")  
public class User {  
    @Id  
    @GeneratedValue(strategy = GenerationType.IDENTITY)  
    @Column(name = "user_seq", nullable = false)  
    Integer userSeq;  
  
    @Column(name = "id", length = 50, nullable = false)  
    String id;  
  
    @Column(name = "regist_time", nullable = false)  
    LocalDateTime registTime;  
  
    @Column(name = "last_login_time")  
    LocalDateTime lastLoginTime;  
}
```

 필자는 MariaDB 에서 auto_increment 를 사용하여 sequence를 생성하고 있기 때문에 위와 같이 IDENTITY 속성을 적용하였다.
  
---
  
# 연결문서
- [@Entity](../../jpa/jpa-@Entity)