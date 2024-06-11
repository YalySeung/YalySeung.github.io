---
title : "@Inheritance"
excerpt : "@Inheritance"
toc : true
toc_sticky : true
toc_label : "@Inheritance"
categories:
- JPA
tags:
- [Querydsl, Spring, JPA, Database]
last_modified_at: 2024-05-29T08:00:00-10:00:00
---
  
---
  
 [JPA](../../jpa/jpa-JPA)에서 **@Inheritance** Annotation은 상속 관계에 있는 Entity들을 데이터베이스에 어떻게 매핑할지 정의하는데 사용된다. 이를 통해 **객체 지향 프로그래밍의 상속 개념을 데이터베이스 테이블 구조에 반영** 할 수 있다. @Inheritance Annotation은 **주로 부모 클래스에 사용**되며, 다양한 전략을 통해 상속 관계를 정의할 수 있다.
  
## @Inheritance 전략
 JPA는 상속 관계를 매핑하기 위해 **세 가지** 주요 전략을 제공한다.
 
 첫째, **SINGLE_TABLE 전략**이다. 이 전략은 **상속 관계에 있는 모든 엔티티를 하나의 테이블에 저장**한다. 테이블에는 [DTYPE](../../jpa/jpa-DTYPE)이라는 특별한 컬럼을 추가하여 각 행이 어떤 엔티티 타입인지 구분한다. 
 이 전략은 Join 이 필요 없기 때문에 **성능이 좋고**, **테이블 개수를 줄일 수 있다**는 장점이 있다. 반면에 **테이블 자체가 커질 우려**가 있고, 테이블이 **데이터 중에는 다수의 null값이 존재**할 것이다.
  
```java
@Entity  
@Inheritance(strategy = InheritanceType.SINGLE_TABLE)  
@DiscriminatorColumn(name = "DTYPE")  
public class Task {  
    @Id  
    @GeneratedValue(strategy = GenerationType.IDENTITY)  
    private Long id;  
    // 공통 필드들  
}  
  
@Entity  
public class TaskResult extends Task {  
    
}  
  
@Entity  
public class StatisticsTask extends Task {  
    
}
```

 둘째, **JOINED 전략**이다. 이 전략은 **부모 클래스와 자식 클래스 각각에 테이블을 생성**하고, **상속된 필드들은 부모 테이블**에, 각 자식 클래스의 **고유 필드는 자식 테이블에 저장**한다. 쿼리 시 **부모 테이블과 자식 테이블을 조인하여 데이터를 조회**한다.
 이 전략은 데이터 **정규화**가 이루어지고, 각 **테이블의 크기가 작아진다**는 장점이 있으나, Join 연산이 필요하여 **성능이 떨어질 수 있다**.
  
```java
@Entity  
@Inheritance(strategy = InheritanceType.JOINED)  
public class Task{  
    @Id  
    @GeneratedValue(strategy = GenerationType.IDENTITY)  
    private Long id;  
    // 공통 필드들  
}  
  
@Entity  
public class TaskResult extends Task {  
    
}  
  
@Entity  
public class StatisticsTask extends Task {  
    
}
```

 셋째, **TABLE_PER_CLASS 전략**이다. 이 전략은 각 클래스마다 별도의 테이블을 생성한다. 자식 클래스 테이블에는 부모 클래스의 필드도 포함된다.
 이 전략은 Join이 없어 성능이 좋고, 구조가 간단하다는 장점이 있으나, 데이터 중복 또는 공통 필드가 여러 테이블에 중복 저장 된다는 단점이 있다.
  
```java
@Entity  
@Inheritance(strategy = InheritanceType.TABLE_PER_CLASS)  
public class Task{  
    @Id  
    @GeneratedValue(strategy = GenerationType.IDENTITY)  
    private Long id;  
    // 공통 필드들  
}  
  
@Entity  
public class TaskResult extends Task {  
    // TaskResult만의 필드들  
}
```

---
  
# 연결문서
- [DTYPE](../../jpa/jpa-DTYPE)
- [JPA](../../jpa/jpa-JPA)