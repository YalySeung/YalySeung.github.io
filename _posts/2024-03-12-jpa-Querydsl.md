---
title : "Querydsl"
excerpt : "Querydsl"
toc : true
toc_sticky : true
toc_label : "Querydsl"
categories:
- JPA
tags:
- [Spring, Database, JPA, Querydsl]
last_modified_at: 2024-03-12T08:00:00-10:00:00
---
  
---
  
## 정의
 이 글에서는 Querydsl Framework 에 대해서 알아보겠다.

> **Querydsl이란?**  
>
> Query Domain Specific Language의 약어로 Hibernate Query Language를 타입에 맞게 생성 및 관리해주는 Builder Opensource Framework이다. 
{: .notice--info}  

 Mybatis로 작성된 Query를 보면, IDE에서 어느정도 정합성 체크를 해주지만 실제 쿼리가 잘 동작하는지는 Query를 호출해 봐야 결과를 알 수 있다. 
 
 반면, Querydsl은 **java 소스로 쿼리를 작성**할 수 있어, **컴파일 시점에 Syntax Error 확인** 가능하다. java 소스 기반이기에 **IDE의 자동완성 기능도 사용** 할 수 있다. 또한 **재사용이 가능하도록 프로그래밍** 할 수 있다. InlineView나 union 등의 기능은 사용이 안된다는 단점이 있지만, 이 또한 우회하여 처리할 수 있는 방법들이 있다. 
  
## Keyword
  
### fetch
- select 쿼리 결과 반환

| Method         | 기능                                     |
| -------------- | -------------------------------------- |
| fetch()        | 조회 결과 Collection  반환                   |
| fetchOne()     | 조회 결과가 한건일 경우 반환                       |
| fetchFirst()   | 조회 대상에 한건 이상일 경우에 한건만 반환               |
| fetchCount()   | 개수 조회, Long                            |
| fetchResults() | 조회한 리스트 + 전체 개수를 포함한 QueryResult 객체 반환 |
  
### where
- 대상 테이블 식별 조건

| Method        | 기능                        |
| ------------- | ------------------------- |
| eq()          | ==                        |
| ne()          | !=                        |
| not()         | 앞의 내용 부정                  |
| isNotNull()   | Null 이 아닌지 확인             |
| in()          | in                        |
| notIn()       | not in                    |
| between(a, b) | 크기가 a와 b 사이 인지            |
| before()      | 시간 전                      |
| after()       | 시간 후                      |
| goe()         | greater than or equal     |
| gt()          | greater than              |
| loe()         | less than or equal        |
| lt()          | less than                 |
| like()        | like 문법, 확인 문자열에 %가 있어야 함 |
| contains()    | like 문법, 문자열 양끝에 % 포함     |
| startsWith()  | like 문법, 문자열 끝에 % 포함      |
| endsWith()    | like 문법, 문자열 시작에 %포함      |
  
## Example
  
```java
String productName = "myProduct";

List<Product> result = queryFactory
        .select(product)
        .from(product)
        .where(product.name.eq(productName), product.price.eq("1000"))
        .fetch();
```
  
## 프로젝트 설정
  
```java
@Configuration  
public class QuerydslConfiguration {  
    @PersistenceContext  
    private EntityManager entityManager;  
  
    @Bean  
    public JPAQueryFactory jpaQueryFactory() {  
        return new JPAQueryFactory(entityManager);  
    }  
}
```
  
```java
//build.gradle v1

project(":rpa-view:view-core") {  
    apply plugin: "eclipse-wtp"  
    dependencies {  
		lib."spring-data-jpa",
		lib."querydsl-jpa",
		lib."querydsl-apt", 
		lib."querydsl-core"  

		...
		
        annotationProcessor "com.querydsl:querydsl-apt:4.2.1:jpa"  
        annotationProcessor lib."persistence-api"  
        annotationProcessor lib."annotation-api"  
  
        def querydslDir = "$buildDir/generated/querydsl"  
  
        sourceSets {  
            main.java.srcDirs += [ querydslDir ]  
        }  
  
        tasks.withType(JavaCompile) {  
            options.annotationProcessorGeneratedSourcesDirectory = file(querydslDir)  
        }  
  
        clean.doLast {  
            file(querydslDir).deleteDir()  
        }  
    }  
    ...
}
```
  
```groovy
buildscript {  
    ext {  
        // QueryDSL 추가  
        queryDslVersion = "5.0.0"  
    }  
}  
  
plugins {  
    id 'war'  
    id 'java'  
    // QueryDSL  
    id "com.ewerk.gradle.plugins.querydsl" version "1.0.10"  
}  
  
dependencies {  
    implementation 'org.springframework:spring-web:5.3.22'  
    implementation 'javax.servlet:javax.servlet-api:4.0.1'  
    implementation 'org.springframework:spring-webmvc:5.3.8'  
    implementation 'org.springframework:spring-context:5.3.22'  
    
    // Hibernate 관련 의존성  
    implementation 'org.hibernate:hibernate-core:5.5.7.Final'  
    implementation 'org.hibernate:hibernate-entitymanager:5.4.32.Final'  
  
    // JPA 관련 의존성  
    implementation 'javax.persistence:javax.persistence-api:2.2'  
    implementation 'org.hibernate.javax.persistence:hibernate-jpa-2.1-api:1.0.2.Final'  
    implementation 'org.springframework.data:spring-data-jpa:2.5.2'  
    implementation 'org.springframework:spring-aspects:5.3.8'  
  
    // Spring Boot가 아닌 경우 Servlet API 및 JSP 관련 의존성 추가  
    providedCompile 'javax.servlet:jstl:1.2'  
  
    // Querydsl 의존성 추가  
    implementation 'com.querydsl:querydsl-jpa:5.0.0'  
    annotationProcessor 'com.querydsl:querydsl-apt:5.0.0'  
    implementation 'com.querydsl:querydsl-apt:5.0.0:jpa'  
  
    testImplementation 'org.mockito:mockito-core:3.12.4'  
    testImplementation 'org.springframework:spring-test:5.3.8'  
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.8.1'  
  
    // json response 검증  
    implementation 'com.jayway.jsonpath:json-path:2.7.0'  
  ...
}  
  
def querydslDir = "$buildDir/generated/querydsl"  
  
querydsl {  
    jpa = true  
    querydslSourcesDir = querydslDir  
}  
sourceSets {  
    main.java.srcDir querydslDir  
}  
  
configurations {  
    querydsl.extendsFrom compileClasspath  
}  
  
compileQuerydsl{  
    options.annotationProcessorPath = configurations.querydsl  
}  
  
compileJava.dependsOn compileQuerydsl  
  
task cleanQuerydslDir(type: Delete) {  
    delete querydslDir  
}  
  
test {  
    dependsOn cleanQuerydslDir, compileQuerydsl  
    useJUnitPlatform()  
}
```
  
---
  
# 연결문서
- [JPA](../../jpa/jpa-JPA)
- [Hibernate](../../jpa/jpa-Hibernate)
- [ORM](../../servercommon/servercommon-ORM)
- [JPQL](../../jpa/jpa-JPQL)
- [AnnotationProcessor](../../spring/spring-AnnotationProcessor)
