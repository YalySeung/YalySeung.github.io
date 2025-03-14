---
title : "SpringBoot Querydsl"
excerpt : "SpringBoot Querydsl"
toc : true
toc_sticky : true
toc_label : "SpringBoot Querydsl"
categories:
- SpringBoot
tags:
- [SpringBoot, Querydsl]
last_modified_at: 2024-07-24T08:00:00-10:00:00
---
  
---
  
> **Spring Boot에서 Querydsl 적용하기**  
>
>  Spring Boot 프로젝트에서 Querydsl을 설정하고 활용하는 방법을 정리한다. 
{: .notice--info}  

  Querydsl을 사용하면 **JPQL을 객체 지향적으로 작성할 수 있으며, 가독성이 뛰어난 코드로 데이터 조회를 할 수 있다.**
  
## 환경 설정
  
### 1️⃣ Gradle 설정
  Querydsl을 사용하기 위해 Gradle 설정을 추가한다.
  
```groovy
plugins {  
    id 'org.springframework.boot' version '2.5.4'  
    id 'io.spring.dependency-management' version '1.0.11.RELEASE'  
    id 'java'  
    id "com.ewerk.gradle.plugins.querydsl" version "1.0.10" // Querydsl 플러그인 추가  
}

dependencies {  
    implementation "com.querydsl:querydsl-jpa:4.4.0"  
    implementation "com.querydsl:querydsl-apt:4.4.0"  
    compileOnly 'org.projectlombok:lombok:1.18.34'
    annotationProcessor 'org.projectlombok:lombok:1.18.34'
}

// Querydsl에서 사용할 경로 설정  
def querydslDir = "$buildDir/generated/querydsl"  

// Querydsl 설정  
querydsl {  
    jpa = true  
    querydslSourcesDir = querydslDir  
}  

// build 시 Querydsl 소스 포함 설정  
sourceSets {  
    main.java.srcDir querydslDir  
}  

// Querydsl 컴파일 설정  
compileQuerydsl {  
    options.annotationProcessorPath = configurations.querydsl  
}  

// Querydsl이 compileClassPath를 상속하도록 설정  
configurations {  
    compileOnly {  
       extendsFrom annotationProcessor  
    }  
    querydsl.extendsFrom compileClasspath  
}
```
  
### 2️⃣ JPA 설정 (`JPAConfig` 클래스 추가)
  
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
  
## 실습 예제
  
### 3️⃣ Querydsl을 적용할 테이블 (`TB_USR`)
  
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
  
### 4️⃣ Entity 정의 (`User` 클래스)
  
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
  
### 5️⃣ Repository 설정
  
```java
public interface UserRepository extends JpaRepository<User, Long>, CustomUserRepository {  
}
```
  
```java
public interface CustomUserRepository {  
}
```
  
```java
public class UserRepositoryImpl extends RepositoryBase implements CustomUserRepository {  
    public UserRepositoryImpl(JPAQueryFactory queryFactory) {  
        super(queryFactory);  
    }  
}
```
  
### 6️⃣ 단위 테스트
  
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

---
  
# 연결문서
