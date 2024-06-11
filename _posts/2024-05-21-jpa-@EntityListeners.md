---
title : "@EntityListeners"
excerpt : "@EntityListeners"
toc : true
toc_sticky : true
toc_label : "@EntityListeners"
categories:
- JPA
tags:
- [Spring, Querydsl, JPA, 미완료]
last_modified_at: 2024-05-21T08:00:00-10:00:00
---
  
---
  
> **@EntityListener란?**  
>
> Entity Lifecycle의 특정 시점에 호출할 수 있는 콜백을 제공해주는 Annotation이다. 
{: .notice--info}  

| Callback Option | 호출시점      |
| --------------- | --------- |
| @PrePersist     | 영속화 직전    |
| @PostPersist    | 영속화 후     |
| @PostLoad       | 로드 이후     |
| @PreUpdate      | update 이전 |
| @PostUpdate     | update 이후 |
| @PreRemove      | delete 이전 |
| @PostRemove     | delete 이후 |
  
---
  
# 연결문서
