---
title : "@PrePersist"
excerpt : "@PrePersist"
toc : true
toc_sticky : true
toc_label : "@PrePersist"
categories:
- JPA
tags:
- [JPA, Spring, Querydsl, 미완료]
last_modified_at: 2024-05-21T08:00:00-10:00:00
---
  
---
  
 **@PrePersist** Annotation은 JPA Entity 라이프 싸이클의 **콜백을 설정**할 수 있게 돕는다. 이런 종류의 콜백 이벤트를 사용하는 방법은 직접 메서드를 작성하는 방법과 EntityListener를 만드는 방법이 있다.
  
```java
@Entity  
@Table(name = "COM_VAR")  
public class CommonVariable {  
    public CommonVariable(CommonVariable commonVariable) {  
        this.variableValue = commonVariable.variableValue;  
    }  
  
    @PrePersist  
    public void test(){  
        System.out.println(variableValue);
    }
    ...
}
```

---
  
# 연결문서
