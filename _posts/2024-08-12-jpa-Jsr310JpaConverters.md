---
title : "Jsr310JpaConverters"
excerpt : "Jsr310JpaConverters"
toc : true
toc_sticky : true
toc_label : "Jsr310JpaConverters"
categories:
- JPA
tags:
- [Spring, JPA]
last_modified_at: 2024-08-12T08:00:00-10:00:00
---
  
---
  
 프로젝트에 Querydsl을 적용하는 중에 DB의 Datetime 컬럼을 가져올{때, 에러가 발생하여, Converter를 추가하던 중 Jsr310JpaConverters Class를 발견했다. 내용을 확인해보니 시간 관련 컬럼을 변경해주는 다양한 static converter 들을 확인할 수 있었다. 이 유용한 Class에 대해서 좀 더 알아보자.
  
> **Jsr310JpaConverters란?**  
>
> Spring Data JPA 에서 Java 8의 새로운 날짜 및 시간 API 지원을 위해 제공하는 Class이다. 
{: .notice--info}  
  
## 주요 Class
 각 Class의 기능을 알아보자.

| Class                   | 기능                                               |
| ----------------------- | ------------------------------------------------ |
| LocalDateTimeConverter  | java.time.LocalDateTime을 java.sql.Timestamp로 변환  |
| LocalDateConverter      | java.time.LocalDate를 java.sql.Date로 변환           |
| LocalTimeConverter      | java.time.LocalTime을 java.sql.Time으로 변환          |
| ZonedDateTimeConverter  | java.time.ZonedDateTim`을 java.sql.Timestamp로 변환  |
| OffsetDateTimeConverter | java.time.OffsetDateTime을 java.sql.Timestamp로 변환 |
  
## Jsr310JpaConverters 적용
 Spring Boot 를 사용하는 독자의 프로젝트에는 Jsr310JpaConverters이 이미 적용되어 있으니 신경 쓸 필요가 없다. 하지만 SpringMVC를 사용한다면, Jsr310JpaConverters를 bean으로 등록하여 사용하자.
  
```java
public class JpaConfiguration {
	...
	@Bean  
	public Jsr310JpaConverters jpaConverters() {  
	    return new Jsr310JpaConverters();  
	}
	...
}
```
  
---
  
# 연결문서
- [JPA](../../jpa/jpa-JPA)