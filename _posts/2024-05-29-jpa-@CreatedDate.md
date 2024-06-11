---
title : "@CreatedDate"
excerpt : "@CreatedDate"
toc : true
toc_sticky : true
toc_label : "@CreatedDate"
categories:
- JPA
tags:
- [Spring, JPA, 미완료]
last_modified_at: 2024-05-29T08:00:00-10:00:00
---
  
---
  
 서비스를 구현할 때, 계정의 **등록 시간**과 같은 데이터는 생성시점에 현재시간을 Database에 Insert 해야 한다. **@CreatedDate** Annotation은 **생성 날짜를 기본값으로 자동 맵핑해주는 Annotation**으로 필요한 Entity Field에 설정하면 된다.
  
```java
@CreatedDate  
@Column(name = "REG_DT", nullable = false)  
@Convert(converter = DateConverter.class)  
private DateTime registDateTime;
```

---
  
# 연결문서
