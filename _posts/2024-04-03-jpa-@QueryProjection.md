---
title : "@QueryProjection"
excerpt : "@QueryProjection"
toc : true
toc_sticky : true
toc_label : "@QueryProjection"
categories:
- JPA
tags:
- [Spring, Annotation, JPA, 미완료]
last_modified_at: 2024-04-03T08:00:00-10:00:00
---
  
---
  
## Artifact
- com.querydsl.core.annotations
  
## 역할
- [@Entity](../../jpa/jpa-@Entity) 전체가 아니라 select 대상을 지정하여 원하는 값만 조회
- Q타입의 파일을 생성하여, repository에서 querydsl 코드를 작성할때 도움을 줌

> **tip**
>
> Repository에서 값을 반환할 때는 DTO로 변환하는 것을 권장 
{: .notice--primary}  

> **tip**
>
> @QueryProjection은 DTO 기반으로 생성된 QDTO 객체의 생성자를 사용함 
{: .notice--primary}  
  
## 사용법
  
### QueryProjection 선언
  
```java
@Entity  
@NoArgsConstructor  
@Getter @Setter  
@EqualsAndHashCode  
@Table(name = "TB_BZ_API_SVR")  
public class ApiServer {  
    @EmbeddedId  
    private ApiServerCompositeKey apiServerCompositeKey = new ApiServerCompositeKey();  
  
    @QueryProjection  
    public ApiServer(ApiServerCompositeKey apiServerCompositeKey) {  
       this.apiServerCompositeKey = apiServerCompositeKey;  
    }
    ...
}
```
  
### 사용
  
#### 1. Property 접근 방식 - Projections.bean
- setter를 통해 data injection
- 기본 생성자 필요
- DTO와 Entity 필드명이 일치해야함

> **caution**
>
> setter가 없을 경우 객체는 생성되지만 값이 없음 
{: .notice--primary}  
  
#### 2. Field 접근 방식 - Projections.fields
- getter, setter 불필요
- 기본 생성자 필요
- DTO와 Entity 필드명이 일치해야함
  
```java
public List<GroupUserInfo> selectMoveGroupList(GroupMoveSearchForm groupMoveSearchForm) {   
{: .notice}  
    return queryFactory.select(  
                    Projections.fields(  
                            GroupUserInfo.class,  
                            qGroup.groupSequence,  
                            qGroup.groupCode,  
                            qGroup.groupName,  
                            qGroup.modifyDateTime,  
                            qGroup.registerDateTime,  
                            qGroup.useYn  
                    )  
            )  
            .from(qGroup)  
            .where(  
                    qGroup.removeYn.eq("N"),  
                    qGroup.useYn.eq("Y"),  
                    BooleanExpressionCreator.integerIsNotInListIfExist(qGroup.groupSequence, groupMoveSearchForm.getGroupSequenceList()),  
                    getGroupCodeNameLikeIfExist(groupMoveSearchForm.getCodeOrNameInfo())  
            )  
            .orderBy(getOrderSpecifier(groupMoveSearchForm.getSortKey(), groupMoveSearchForm.getSortOrder()))  
            .offset(groupMoveSearchForm.getStartRowNo2())  
            .limit(groupMoveSearchForm.getPageRowCount())  
            .fetch();  
}
```
  
#### 3. 생성자 사용 접근 방식 - Projections.constructor
Class 의 생성자를 이용하는 방식으로 필드명은 일치하지 않아도 되지만, Class **생성자의 매개변수**와 **select 문의 컬럼** 간의 **타입과 순서가 일치**해야 한다.
때에 따라 생성자의 일부 매개변수 값에 null을 입력해야 하는 경우가 있다. 그런 경우에는 [Expressions](../../jpa/jpa-Expressions).constant() 함수를 이용하자.
  
```java
@Data  
public class CommonVariableList extends CommonVariable{  
  
    private String useYnName;  
    private DateTime lastChangedDateTime;  
  
    public CommonVariableList() {  
    }  
    
    @QueryProjection  
    public CommonVariableList(CommonVariable commonVariable) {  
        super(commonVariable);  
        this.useYnName = commonVariable.getUseYn().equals("Y") ? "사용" : "사용 안 함";  
    }  
  
    @QueryProjection  
    public CommonVariableList(Integer variableSequence, String variableName, String variableValue, String variableType, String useYn, String registerId, String modifyId, Integer groupSequence, String apiReadonlyYn, String variableScope, String useYnName, DateTime lastChangedDateTime) {  
        super(variableSequence, variableName, variableValue, variableType, useYn, registerId, modifyId, groupSequence, apiReadonlyYn, variableScope);  
        this.useYnName = useYnName;  
        this.lastChangedDateTime = lastChangedDateTime;  
    }
    ...
}
```
  
```java
@Override  
public List<CommonVariableList> selectAll() {   
{: .notice}  
    return queryFactory.select(Projections.constructor(CommonVariableList.class,  
                    qCommonVariable,  
                    new CaseBuilder().when(qCommonVariable.useYn.eq("Y"))  
                            .then("사용")  
                            .otherwise("사용 안 함")  
                            .as("USE_YN_NAME")  
            ))  
            .from(qCommonVariable)  
            .fetch();  
}
```

---
  
# 연결문서
- [Querydsl](../../jpa/jpa-Querydsl)
- [@Entity](../../jpa/jpa-@Entity)
- [Lombok](../../spring/spring-Lombok)