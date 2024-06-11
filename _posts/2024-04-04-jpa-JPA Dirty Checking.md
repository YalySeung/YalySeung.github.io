---
title : "JPA Dirty Checking"
excerpt : "JPA Dirty Checking"
toc : true
toc_sticky : true
toc_label : "JPA Dirty Checking"
categories:
- JPA
tags:
- [Spring, JPA]
last_modified_at: 2024-04-04T08:00:00-10:00:00
---
  
---
  
## 정의
> **JPA Dirty Checking 이란**  
>
> 영속성 컨테이너가 관리하는 엔티티의 상태를 감지하여, 변경된 부분이 있다면, 트랜잭션이 끝나는 시점에 데이터베이스에 반영하는 기능 
{: .notice--info}  
  
## Dirty Checking LifeCycle
- 영속성 컨텍스트에서 관리되는 Entity를 처음 조회할 때, Snapshot 생성
- Transaction 커밋 되기 전까지 영속성 컨텍스트는 변경사항을 추적하기만 하고, DB에는 반영하지 않음
- Transaction 커밋 시점에 Entity 와 Snapshot을 비교하여 다른점이 있다면 Update Query 전달

> **tip**
>
> Dirty Checking 으로 생성되는 update쿼리는 모든 필드를 업데이트 하는 방식을 기본값으로 사용하는데, @DynamicUpdate Annotation을 사용하면, 변경된 필드만 업데이트 됨 
{: .notice--info}  
  
## Example
  
```java
public void saveTest() { 
	final User EXPECTED_USER = TestInstanceFactory.getUser();
	userRepository.save(EXPECTED_USER);
}
```  
- save 메서드를 호출하면 Entity객체의 상태가 persistent 상태로 변경됨
- 영속성 컨텍스트에 의해 관리되며, 해당 객체의 모든 변경사항이 추적됨
- **EXPECTED_USER 객체를 수정하면 영속성 컨텍스트에 해당 내용이 반영**되며, 필요한 경우 해당 변경사항은 데이터베이스에 반영됨

---
  
# 연결문서
-  [JPA](../../jpa/jpa-JPA)
- [영속성(Persistence)](../../servercommon/servercommon-영속성(Persistence))
- [@Entity](../../jpa/jpa-@Entity)
- [@DynamicUpdate](../../annotation/annotation-@DynamicUpdate)