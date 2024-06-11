---
title : "CustomRepository"
excerpt : "CustomRepository"
toc : true
toc_sticky : true
toc_label : "CustomRepository"
categories:
- JPA
tags:
- [Spring, JPA]
last_modified_at: 2024-04-09T08:00:00-10:00:00
---
  
---
  
## 정의
> **CustomRepository란?**  
>
> Spring Data Jpa 가 제공하는 기본 쿼리 메서드 이외에 복잡한 쿼리 사용을 위한 Interface 
{: .notice--info}  
  
## 구조
  
![image](../../assets/images/CustomRepositoryStructure.png)

> **caution**
>
> 실제 쿼리를 구성하는 UserRepositoryImpl은 CustomUserRepository를 구현하지만 클래스명은 사용할 Repository와 맞춰야 한다. 
{: .notice--info}  
  
## Example
  
```java
public interface UserRepository extends JpaRepository<User, Integer>, CustomUserRepository{   
{: .notice--info}  
//    UserSequenceRepository findUserSequenceByUserIdAndRemoveYn(String userId, String removeYn);  
}
```
  
```java
@Repository  
@Transactional  
public class UserRepositoryImpl implements CustomUserRepository {  
  
    private final JPAQueryFactory queryFactory;  
  
    private final QUser qUser;  
  
    @Autowired  
    public UserRepositoryImpl(JPAQueryFactory queryFactory) {  
        this.queryFactory = queryFactory;  
        this.variable = new QUser("user");  
    }  

	...
    @Override  
    public List<String> selectDepartmentNameListInGroup(Integer groupSequence) {   
{: .notice}  
        return queryFactory.select(qUser.departmentName)  
                .from(qUser)  
				.where(
					qUser.removeYn.eq("N"),
					getGroupIfExist()
				)
                .fetch();  
    }
    
	@Override  
	public Integer initializePassword(List<Integer> usersequncelist, String password) {   
{: .notice}  
	    List<User> userList = queryFactory.selectFrom(qUser)   
{: .notice}  
	            .where(qUser.userSequence.in(usersequncelist))  
	            .fetch();  
	  
	    userList.forEach(user -> {   
{: .notice}  
	        user.setUserPassword(password);  
	        user.setPasswordResetYn("Y");  
	        user.setLastPasswordModifyDateTime(DateTime.now());  
	        user.setModifyDateTime(DateTime.now());  
	    });  
	  
	    return userList.size();  
	}
    ...
}
```

> **tip**
>
> CustomRepository Method 중 update의 경우 좀더 주의를 기울일 필요가 있다. queryFactory의 update 메서드를 사용하면, Persistence Context의 데이터가 갱신되지 않으므로 select 후 반환된 객체를 수정해야한다. 
{: .notice}  
  
### input값의 null 체크
  
```java
private BooleanExpression getGroupIfExist(Integer groupSequence){  
    if (groupSequence > 0) {     
{: .notice}  
        return qUser.groupSequence.eq(groupSequence);
    } else {  
        return null;  
    }  
}
```  
- Where 절에 Parameter로 전달하면 적용됨
  
---
  
# 연결문서
- [Spring Data Jpa](../../jpa/jpa-Spring-Data-Jpa)