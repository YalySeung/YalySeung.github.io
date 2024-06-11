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
> **Querydsl이란?**  
>
> Query Domain Specific Language
> Hibernate Query Language를 타입에 맞게 안전하게 생성 및 관리해주는 Builder Opensource Framework 
{: .notice--info}  
  
## 장점
- java 소스로 쿼리를 작성할 수 있어, 컴파일 시점에 Syntax Error 확인 가능
- IDE의 자동완성 기능 사용 가능
- 복잡한 Query와 동적 Query 작성이 용이함
- Query 작성 시, 제약조건등을 메서드로 추출하여 재사용 가능
  
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
{: .notice}  
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
//build.gradle

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
  
---
  
# 연결문서
- [JPA](../../jpa/jpa-JPA)
- [Hibernate](../../jpa/jpa-Hibernate)
- [ORM](../../servercommon/servercommon-ORM)
- [JPQL](../../jpa/jpa-JPQL)
- [AnnotationProcessor](../../spring/spring-AnnotationProcessor)
- [성능관련 주의사항](https://hyune-c.tistory.com/36)
- [참고링크](https://kha0213.github.io/jpa/querydsl/)
- [설정](https://www.devkuma.com/docs/spring-data-jpa/query-dsl/)