---
title : "Spring Data JPA"
excerpt : "Spring Data JPA"
toc : true
toc_sticky : true
toc_label : "Spring Data JPA"
categories:
- JPA
tags:
- [Spring, JPA]
last_modified_at: 2024-04-04T08:00:00-10:00:00
---
  
---
  
## 정의
> **Spring Data Jpa란?**  
>
> JPA가 제공하는 공통적인 기능을 인터페이스로 추출한 라이브러리
>  
{: .notice--info}  
  
## Core Method

| Method                    | 기능          |
| ------------------------- | ----------- |
| save(S entity)            | Entity 저장   |
| findById(ID primaryKey)   | ID로 검색      |
| findAll()                 | 전체검색        |
| count()                   | Tuple 개수 검색 |
| delete(T entity)          | 삭제          |
| existsById(ID primaryKey) | 존재 여부 확인    |
  
## NamingConvention으로 쿼리 생성
JPA에서 정의해 놓은 NamingConvention을 활용하면 내용을 구현하지 않아도 어느정도 수준의 [JPQL](../../jpa/jpa-JPQL)을 생성해준다

| Keyword            | Sample                                                    | JPQL                                                                      |
| ------------------ | --------------------------------------------------------- | ------------------------------------------------------------------------- |
| Distinct           | findDistinctByLastnameAndFirstname                        | select distinct \<columnName\> where x.lastname = ?1 and x.firstname = ?2 |
| And<br>            | findByLastnameAndFirstname                                | select distinct \<columnName\> where x.lastname = ?1 and x.firstname = ?2 |
| Or                 | findByLastnameOrFirstname                                 | select distinct \<columnName\> where x.lastname = ?1 or x.firstname = ?2  |
| Is, Equal          | findByFirstname, findByFirstnameIs, findByFirstnameEquals | ... where x.firstname = ?1                                                |
| LessThan           | findByAgeLessThan                                         | ... where x.age < ?1                                                      |
| LessThanEqual      | findByAgeLessThanEqual                                    | ... where x.age <= ?1                                                     |
| GreaterThan        | findByAgeGreaterThan                                      | ... where x.age > ?1                                                      |
| GreaterThanEqual   | findByAgeGreaterThanEqual                                 | ...... where x.age >= ?1                                                  |
| Between            | findByStartDateBetween                                    | ... where x.startDate beween ?1 and ?2                                    |
| After              | findByStartDateAfter                                      | ... where x.startDate > ?1                                                |
| Before             | findByStartDateBefore                                     | ... where x.startDate < ?1                                                |
| IsNull, Null       | findByAge(Is)Null                                         | ... where x.age is null                                                   |
| isNotNull, NotNull | findByAge(Is)NotNull                                      | ... where x.age is not null                                               |
| Like               | findByFirstnameLike                                       | ... where x.firstname like ?1                                             |
| NotLike            | findByFirstnameNotLike                                    | ... where x.firstname not like ?1                                         |
| StartingWith       | findByFirstnameStartingWith                               | ... where x.firstname like ?1                                             |
| EndingWith         | findByFirstnameEndingWith                                 | ... where x.firstname like ?1                                             |
| Contating          | findByFirstnameContating                                  | ... where x.firstname like ?1                                             |
| OrderBy            | findByAgeOrderByLastnameDesc                              | … where x.age = ?1 order by x.lastname desc                               |
| Not                | findByLastnameNot                                         | … where x.lastname <> ?1                                                  |
| In                 | findByAgeIn(Collection\<Age\> ages)                       | … where x.age in ?1                                                       |
| NotIn              | findByAgeNotIn(Collection\<Age\> ages)                    | … where x.age not in ?1                                                   |
| True               | findByActiveTrue()                                        | … where x.active = true                                                   |
| False              | findByActiveFalse()                                       | … where x.active = false                                                  |
| IgnoreCase         | findByFirstnameIgnoreCase                                 | … where UPPER(x.firstname) = UPPER(?1)                                    |
  
## 프로젝트 설정
  
```java
@Configuration  
@EnableJpaRepositories(basePackages = "<패키지명>.api.repository")  
@EnableJpaAuditing  
@EnableTransactionManagement  
public class JpaConfiguration {  
  
    @Value("#{apiProperties['jdbc.dataSourceType']}")  
    private String dataSourceType;  
  
    @Value("#{apiProperties['jdbc.jndiName']}")  
    private String jndiName;  
  
    @Bean  
    public DataSource dataSourceForJPA() {  
        return DataSourceInitializer.getDataSource(dataSourceType, jndiName);  
    }  
  
    @Bean  
    public LocalContainerEntityManagerFactoryBean entityManagerFactory(@Qualifier("dataSourceForJPA")DataSource dataSource) {  
        LocalContainerEntityManagerFactoryBean em = new LocalContainerEntityManagerFactoryBean();  
        em.setDataSource(dataSource);  
        //em.setPackagesToScan(new String[]{"<패키지명1>", "<패키지명2>"});
        em.setPackagesToScan("org.infinity.server.entity");
        em.setPersistenceProviderClass(HibernatePersistenceProvider.class);  
        return em;  
    }  
  
    @Bean  
    public JpaTransactionManager  transactionManager(EntityManagerFactory entityManagerFactory) {  
        JpaTransactionManager jpaTransactionManager = new JpaTransactionManager();  
        jpaTransactionManager.setEntityManagerFactory(entityManagerFactory);  
        return jpaTransactionManager;  
    }  
  
    @Bean  
    public Jsr310JpaConverters jpaConverters() {  
        return new Jsr310JpaConverters();  
    }  
}
```

> **caution**
>
> Entity가 정상적으로 스캔되기 위해서는 **setPackagesToScan()**으로 등록된 패키지 내에 위치해야한다. 
{: .notice--info}  

---
  
# 연결문서
- [@EnableJpaRepositories](../../jpa/jpa-@EnableJpaRepositories)
- [JPA](../../jpa/jpa-JPA)
- [JPQL](../../jpa/jpa-JPQL)
- [CustomRepository](../../jpa/jpa-CustomRepository)
- [Querydsl](../../jpa/jpa-Querydsl)
- [BooleanBuilder](../../jpa/jpa-BooleanBuilder)
- [BooleanExpression](../../jpa/jpa-BooleanExpression)
- [공식가이드 문서](https://docs.spring.io/spring-data/jpa/reference/repositories/query-by-example.html)