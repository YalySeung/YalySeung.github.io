---
title : "SpringBoot Swagger"
excerpt : "SpringBoot Swagger"
toc : true
toc_sticky : true
toc_label : "SpringBoot Swagger"
categories:
- SpringBoot
tags:
- [SpringBoot]
last_modified_at: 2024-07-26T08:00:00-10:00:00
---
  
---
  
> **Spring Boot에서 Swagger 적용하기**  
>
>  Spring Boot 프로젝트에서 API 문서를 자동으로 생성하고 관리하는 방법이다. 
{: .notice--info}  

  Swagger는 **API 문서를 자동으로 생성하여 개발자 간의 협업을 돕고, API 테스트를 쉽게 수행할 수 있도록 지원한다.**
  
## 환경 설정
  
### 1️⃣ Gradle 의존성 추가
  
```groovy
dependencies {
    implementation 'org.springdoc:springdoc-openapi-ui:1.6.9'  
    implementation 'org.springdoc:springdoc-openapi-data-rest:1.6.9'
}
```
  
### 2️⃣ Swagger 설정 파일 (`SwaggerConfig`)
  
```java
@Configuration  
public class SwaggerConfig {  
    @Bean  
    public OpenAPI openAPI() {  
        return new OpenAPI()  
                .components(new Components())  
                .info(apiInfo());  
    }  

    private Info apiInfo() {  
        return new Info()  
                .title("SAMPLE API")  
                .description("샘플 API 입니다.")  
                .version("1.0.0");  
    }  
}
```
  
## Swagger UI 확인
  위 설정이 완료되면, **WAS 실행 후** `http://<ip>:<port>/swagger-ui.html`에 접속하면 자동으로 생성된 API 문서를 확인할 수 있다.
  
## API 문서에 추가 정보 설정
  
### 3️⃣ API 엔드포인트에 설명 추가
  
```java
@RestController  
@RequestMapping("/test")  
@Tag(name = "테스트 API", description = "API 동작을 테스트하는 엔드포인트")  
public class TestController {  

    @GetMapping("/string")  
    @Operation(summary = "String Response 테스트", description = "String 응답이 정상적으로 생성되는지 확인")  
    public String testString() {  
        return "test";  
    }  
}
```
  
### 4️⃣ 응답 객체에 추가 정보 설정 (`@Schema`)
  
```java
@Schema(description = "테스트 응답 객체")  
public class TestResponse {  
    @Schema(description = "사용자 이름", example = "홍길동")  
    private String name;  
    @Schema(description = "사용자 전화번호", example = "010-1234-5678")  
    private String phoneNumber;  
}
```
  
## Swagger 문서에서 API 숨기기
  특정 API를 Swagger 문서에서 제외하고 싶다면 `@Hidden` 어노테이션을 적용하면 된다.
  
```java
@Hidden  
@GetMapping("/private")  
public String hiddenApi() {  
    return "이 API는 Swagger에 노출되지 않습니다.";  
}
```
  
## 멀티파트 파일 업로드 설정
  파일 업로드 기능을 사용할 경우 `application.properties`에 설정을 추가해야 한다.
  
```properties
spring.servlet.multipart.enabled=true
spring.servlet.multipart.max-file-size=10MB
spring.servlet.multipart.max-request-size=10MB
```

  또한, `@PutMapping` 또는 `@PostMapping`에서 `consumes` 값을 설정해야 한다.
  
```java
import org.springframework.http.MediaType;

@PutMapping(value = "", consumes = MediaType.MULTIPART_FORM_DATA_VALUE)
```
  
## 장점과 단점
  
### ✅ 장점
- **자동으로 API 문서를 생성**하여 유지보수가 용이  
- **API 테스트를 쉽게 수행****  
- 스펙을 기반으로 다양한 API 클라이언트와 연동 가능  
  
### ❌ 단점
- **보안 설정을 추가하지 않으면 민감한 API 정보가 노출될 가능성이 있음==  
- 설정 파일이 다소 길어질 수 있음  

---
  
# 연결문서
- [Swagger](../../servercommon/servercommon-Swagger)
- [SpringBoot-Project](../../springboot/springboot-SpringBoot-Project)
