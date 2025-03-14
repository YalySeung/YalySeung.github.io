---
title : "@QueryProjection"
excerpt : "@QueryProjection"
toc : true
toc_sticky : true
toc_label : "@QueryProjection"
categories:
- JPA
tags:
- [Spring, Annotation, JPA]
last_modified_at: 2024-04-03T08:00:00-10:00:00
---
  
---
  
## Artifact
- `com.querydsl.core.annotations`
  
## 역할
- **`@Entity` 전체가 아니라 특정 필드만 조회하도록 지정**  
- **Q타입의 파일을 생성하여 Querydsl 코드 작성 시 도움을 줌**  

> **tip**
>
> Repository에서 값을 반환할 때는 DTO로 변환하는 것을 권장 
{: .notice--primary}  

> **tip**
>
> `@QueryProjection`은 DTO 기반으로 생성된 QDTO 객체의 생성자를 사용함 
{: .notice--primary}  
  
## 사용법
  
### 1️⃣ `@QueryProjection` 선언
  
```java
import com.querydsl.core.annotations.QueryProjection;

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
}
```
  
## Querydsl Projections 사용법
  
### 2️⃣ Property 접근 방식 - `Projections.bean`
- Setter를 통해 데이터 주입
- 기본 생성자 필요
- DTO와 Entity 필드명이 일치해야 함

> **caution**
>
> Setter가 없을 경우 객체는 생성되지만 값이 없음 
{: .notice--primary}  
  
### 3️⃣ Field 접근 방식 - `Projections.fields`
- Getter, Setter 불필요
- 기본 생성자 필요
- DTO와 Entity 필드명이 일치해야 함
  
```java
public List<GroupUserInfo> selectMoveGroupList(GroupMoveSearchForm groupMoveSearchForm) {  
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
            .where(qGroup.removeYn.eq("N"), qGroup.useYn.eq("Y"))  
            .orderBy(qGroup.groupSequence.desc())  
            .fetch();  
}
```
  
### 4️⃣ 생성자 접근 방식 - `Projections.constructor`
- 생성자의 매개변수 순서와 `select` 컬럼 순서가 일치해야 함
  
```java
@Data  
public class CommonVariableList extends CommonVariable {  
    private String useYnName;  
    private DateTime lastChangedDateTime;  

    @QueryProjection  
    public CommonVariableList(CommonVariable commonVariable) {  
        super(commonVariable);  
        this.useYnName = commonVariable.getUseYn().equals("Y") ? "사용" : "사용 안 함";  
    }  
}
```
  
```java
@Override  
public List<CommonVariableList> selectAll() {  
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
