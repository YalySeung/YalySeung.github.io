---
title : "SpringBoot Querydsl"
excerpt : "SpringBoot Querydsl"
toc : true
toc_sticky : true
toc_label : "SpringBoot Querydsl"
categories:
- SpringBoot
tags:
- [SpringBoot, Querydsl, 미완료]
last_modified_at: 2024-07-24T08:00:00-10:00:00
---
  
---
  
 SpringBoot 프로젝트에 Querydsl을 적용해보자.
  
## 환경 설정
 먼저 Querydsl 종속성을 가져오기 위해 Gradle 설정이 필요하다. 필자는 jdk 1.8 기준으로 프로젝트를 생성할 것이기 때문에 호환 가능한 4.2.1 버전을 사용하겠다.
  
```groovy
plugins {  
    id 'org.springframework.boot' version '2.5.4'  
    id 'io.spring.dependency-management' version '1.0.11.RELEASE'  
    id 'java'  
    id "com.ewerk.gradle.plugins.querydsl" version "1.0.10" // querydsl 플러그인 추가  
}

dependencies {  
	//...
    implementation "com.querydsl:querydsl-jpa:4.4.0"  
    implementation "com.querydsl:querydsl-apt:4.4.0"  
	//...
	compileOnly 'org.projectlombok:lombok:1.18.34'
	annotationProcessor 'org.projectlombok:lombok:1.18.34'
}

// querydsl에서 사용할 경로 설정(현재 지정한 부분은 .gitignore에 포함됨)  
def querydslDir = "$buildDir/generated/querydsl"  
  
// JPA 사용 여부 및 사용할 경로 설정  
querydsl {  
    jpa = true  
    querydslSourcesDir = querydslDir  
}  
  
// build 시 사용할 sourceSet 추가 설정  
sourceSets {  
    main.java.srcDir querydslDir  
}  
  
// querydsl 컴파일 시 사용할 옵션 설정  
compileQuerydsl{  
    options.annotationProcessorPath = configurations.querydsl  
}  
  
// querydsl이 compileClassPath를 상속하도록 설정  
configurations {  
    compileOnly {  
       extendsFrom annotationProcessor  
    }  
    querydsl.extendsFrom compileClasspath  
}
```

 종속성 설정이 끝났다면 JPA 설정을 해보도록 하자. JPAConfig Class 를 추가한다.
  
```java
@Configuration  
@EnableJpaAuditing  
public class JPAConfig {  
   
    @PersistenceContext  
    private EntityManager em;  
  
	@Bean  
    public JPAQueryFactory jpaQueryFactory() {  
        return new JPAQueryFactory(em);  
    }  
}
```
  
## Example
 설정이 모두 완료되었으니 실습을 해보자. 아래는 Querydsl을 적용할 Table 정보이다.
  
```sql
create table TB_USR  
(  
	USR_SEQ bigint(38) auto_increment comment '고객 순번'  
	primary key,  
	USR_NM varchar(50) default '' not null comment '고객 명',  
	USR_RN varchar(13) default '' not null comment '고객 주민등록 번호'  
)  
comment '고객정보';
```
  
### Entity
 먼저 Table에서 가져올 데이터를 정의할 Entity를 정의해보자.
  
```java
@Entity  
@Table(name = "TB_USR")  
@Getter @Setter  
@NoArgsConstructor  
public class User {  
    @Id  
    @GeneratedValue(strategy = GenerationType.IDENTITY)  
    @Column(name = "USR_SEQ")  
    private Long id;  
  
    @Column(name = "USR_NM", nullable = false, columnDefinition = "VARCHAR(50) DEFAULT ''")  
    private String name;  
  
    @Column(name = "USR_RN", nullable = false, columnDefinition = "VARCHAR(13) DEFAULT ''")  
    private String registrationNumber;  
}
```

 Class를 추가한 후 Gradle > other > compileQuerydsl 을 실행하면 Entity에 대응하는 QClass가 만들어진다.
  
![image](../../assets/images/CompileQClass.png)
  
### Repository
 다음은 DB 데이터 처리를 위한 Repository를 만들 차례다. JpaRepository 에서 제공하는 기본 쿼리 이외에 나만의 쿼리를 추가하고 싶다면 기본적으로 3개의 Class를 만들어야 한다.
  
![image](../../assets/images/CustomRepositoryStructure.png)
  
```java
public interface UserRepository extends JpaRepository<User, Long>, CustomUserRepository {  
}
```
  
```java
public interface CustomUserRepository {  
}
```
  
```java
public class UserRepositoryImpl extends RepositoryBase implements CustomUserRepository{  
    public UserRepositoryImpl(JPAQueryFactory queryFactory) {  
        super(queryFactory);  
    }  
}
```

 필자는 구현 class마다 Annotation을 추가하는게 귀찮아서 추상 클래스 하나를 더 만들었다.
  
```java
@Repository  
public abstract class RepositoryBase {  
    protected final JPAQueryFactory queryFactory;  
  
    @Autowired  
    public RepositoryBase(JPAQueryFactory queryFactory) {  
        this.queryFactory = queryFactory;  
    }  
}
```
  
### 단위테스트
 User Table에 테스트 데이터를 insert 한 후 정상적으로 조회 되는지 테스트한다.
  
```java
@SpringBootTest  
@SpringJUnitConfig  
class UserRepositoryTest {  
    @Autowired  
    private UserRepository userRepository;  
  
    @Test  
    public void testSaveAndFindById() {  
        User user = new User("홍길동", "010-1111-1111");  
        User savedUser = userRepository.save(user);  
  
        User foundUser = userRepository.findById(savedUser.getId()).orElse(null);  
        assertThat(foundUser).isNotNull();  
        assertThat(foundUser.getName()).isEqualTo("홍길동");  
    }  
}
```
  
![image](../../assets/images/SpringBootRepositoryTestResult.png)
  
---
  
# 연결문서
