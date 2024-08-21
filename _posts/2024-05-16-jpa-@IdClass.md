---
title : "@IdClass"
excerpt : "@IdClass"
toc : true
toc_sticky : true
toc_label : "@IdClass"
categories:
- JPA
tags:
- [Spring, Annotation, 미완료, JPA, Querydsl]
last_modified_at: 2024-05-16T08:00:00-10:00:00
---
  
---
  
 이 글에서는 [@Entity](../../jpa/jpa-@Entity) Class에 복합 기본 키를 지정 할 때, 사용하는 @IdClass Annotation에 대해서 알아보겠다.

 필자는 **Table마다 고유 Sequence를 사용**하는 것을 선호하지만, 상황에 따라 또는 As-Is 프로그램의 구조상 어쩔 수 없이 복합키를 사용해야 하는 경우가 있다.

 Entity에 복합키를 지정하는 방법이 @IdClass Annotation만 있는 것은 아니다. [@EmbeddedId](../../jpa/jpa-@EmbeddedId) 와 [@Embeddable](../../jpa/jpa-@Embeddable) Annotation을 사용하여 복합 키를 가진 Entity를 구성할 수 있다. 그러나 Key Class와 Entity Class가 분리되는 구조가 되기 때문에 QueryDsl을 사용하여 Custom 쿼리를 작성하는데 불편함이 생긴다. 그리고 복합키의 내용을 확인하려면 복합키 클래스에 접근해야 한다.

 반면 @IdClass는 별도의 키 클래스를 지정하며, 이 클래스는 기본 키를 구성하는 필드들을 포함한다. 필자의 생각에는 이 방법이 가독성과 Querydsl 사용 측면에서 장점이 좀더 많다고 생각한다. 샘플 코드를 한번 살펴보자.
  
## @IdClass를 사용한 복합키 Entity
 필자는 게임 장비 정보와 대응하는 Entity를 구성할 예정이다. 필요한 정보는 장비명, 등급, 장비 설명 등이 있을 것이다. 이 중 장비명과 등급을 복합키로 사용하겠다.

 먼저 복합키로 사용할 장비명과 등급을 별도 클래스로 분리하여 선언한다.
  
```java
@NoArgsConstructor @AllArgsConstructor  
@Data  
public class EquipmentCompositeKey implements Serializable {  
    @Column(name = "NAME", nullable = false)  
    private String name;  
  
    @Column(name = "RANK", nullable = false)  
    private Integer rank;  
}
```

 여기서 주의할 점은 java.io의 Serializable 인터페이스를 구현해야 하며, Equals 와 hashcode를 선언해주어야 한다는 점이다. 필자는 [@Data](../../annotation/annotation-@Data) Annotation 을 사용하였다. 

 그리고 @IdClass를 사용한 Entity Class를 선언한다.
  
```java
@Entity  
@NoArgsConstructor @AllArgsConstructor  
@Getter @Setter  
@IdClass(EquipmentCompositeKey.class)  
public class StatisticsProcessStatusInlineView {  

    @Id  
    @Column(name = "NAME", nullable = false)  
    private String name;  
  
    @Id  
    @Column(name = "RANK", nullable = false)  
    private Integer rank;  
  
    @Column(name = "EXPLANATION")  
    private String explanation;  
}
```
  
---
  
# 연결문서
- [@EmbeddedId](../../jpa/jpa-@EmbeddedId)