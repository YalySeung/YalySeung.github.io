---
title : "@Transient"
excerpt : "@Transient"
toc : true
toc_sticky : true
toc_label : "@Transient"
categories:
- JPA
tags:
- [Spring, Annotation, JPA]
last_modified_at: 2024-04-05T08:00:00-10:00:00
---
  
---
  
 JPA [@Entity](../../jpa/jpa-@Entity) 를 추가하다보면 DB에는 존재하는 않는 컬럼이지만 Entity 객체에서 사용해야 하는 변수가 있을 수 있다. JPA 에러를 방지하려면 이런 변수에 @Transient Annotation을 추가해야 한다.
  
```java
@Entity  
@NoArgsConstructor  
@AllArgsConstructor  
@Data  
@Table(name = "BAT_SCDL")  
public class BatchJob implements Comparable<BatchJob> {   
{: .notice}  
    @Id  
    @Column(name = "BAT_TYPE_CD", length = 30, nullable = false)  
    private String batchJobTypeCode;  
    @Column(name = "BAT_NM", length = 50, nullable = false)  
    private String batchJobName;  
    @Transient  
    private String batchJobExecutingInfoText;
}
```

 간단한 예시는 살펴보면 위와 같다.

---
  
# 연결문서
