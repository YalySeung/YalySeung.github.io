---
title : "SpringBoot Project"
excerpt : "SpringBoot Project"
toc : true
toc_sticky : true
toc_label : "SpringBoot Project"
categories:
- SpringBoot
tags:
- [SpringBoot]
last_modified_at: 2023-11-13T08:00:00-10:00:00
---
  
---
  
 이 글에서는 SpringBoot API 서버를 구성해볼 예정이다.
  
## 환경 설정
 먼저 새 Gradle 프로젝트를 생성하여 의존성을 설정하자
  
```groovy
dependencies {  
	// Web App 개발을 위한 기본 설정과 종속성 제공
    implementation 'org.springframework.boot:spring-boot-starter-web'  

	// Spring JPA 설정 제공
    implementation 'org.springframework.boot:spring-boot-starter-data-jpa'  

	// 입력 검증 지원
    implementation 'org.springframework.boot:spring-boot-starter-validation'  

	// MariaDB 사용
    implementation 'org.mariadb.jdbc:mariadb-java-client'  
  
	// DB 연결 전 경량 내장 DB 사용
    runtimeOnly 'com.h2database:h2' // H2 데이터베이스 의존성 추가  

	// lombok 사용
	compileOnly 'org.projectlombok:lombok:1.18.34'  
	annotationProcessor 'org.projectlombok:lombok:1.18.34'

	// Spring Boot Test 사용에 필요한 기본 설정
    testImplementation 'org.springframework.boot:spring-boot-starter-test'  
    testImplementation 'org.springframework.security:spring-security-test'  
}
```
  
## Debug 실행
 Spring Boot 는 내장 Tomcat을 제공하기 때문에 Spring MVC 처럼 Tomcat을 직접 설정할 필요가 없다 대신 application.properties 파일에 간단한 정보를 입력한다.
  
```xml
spring.application.name=edocserver  

// 서비스가 구동될 port
server.port=8080  

// H2 사용
//spring.datasource.url=jdbc:h2:mem:testdb
//spring.datasource.driverClassName=org.h2.Driver
//spring.datasource.username=sa
//spring.datasource.password=password

// Mariadb 사용
//spring.datasource.url=jdbc:mariadb://localhost:3309/edoc  
//spring.datasource.driverClassName=org.mariadb.jdbc.Driver  
//spring.datasource.username=edoc  
//spring.datasource.password=qwer1234  
  
spring.jpa.properties.hibernate.show_sql=true  
spring.jpa.properties.hibernate.format_sql=true  
spring.jpa.properties.hibernate.use_sql_comments=true  
  
spring.jpa.hibernate.ddl-auto=update
```

 실행은 Applcation 진입점인 Application Class에 우클릭 후 실행한다.
  
```java
@SpringBootApplication  
public class EdocserverApplication {  
    public static void main(String[] args) {  
       SpringApplication.run(EdocserverApplication.class, args);  
    }  
}
```
  
## Controller 추가
 SpringBoot는 경량 API 서버 개발을 위한 Framework 이기 때문에 Controller를 간단히 추가 할 수 있다.
  
```java
@RestController  
@RequestMapping("/test")  
public class TestController {  
	@GetMapping("/string")  
	public String testString(){  
	    return "test";  
	}  
	  
	@GetMapping("/json")  
	public TestResponse getUserInfo(){  
	    return new TestResponse("홍길동", "010-3333-3333");  
	}  
	  
	@PostMapping("/json/withbody")  
	public TestResponse getEchoUserInfo(@RequestBody TestRequest request){  
	    return new TestResponse(request.getName(), request.getRegistrationNumber());  
	}
}
```

 String 반환은 물론 [@RestController](../../annotation/annotation-@RestController) Annotation만 사용하면 Json 데이터도 반환이 가능하다.
  
![image](../../assets/images/SpringBootJsonResponse.png)

---
  
# 연결문서
- [Intellij](../../ide/ide-Intellij)
- [Vue-프로젝트-Init](../../vuestudy/vuestudy-Vue-프로젝트-Init)
- [Vue-환경변수](../../vuestudy/vuestudy-Vue-환경변수)
- [npm](../../nodejs/nodejs-npm)