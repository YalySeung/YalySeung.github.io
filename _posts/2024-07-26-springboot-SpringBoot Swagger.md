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
  
 이 글에서는 SpringBoot 프로젝트에 Swagger를 적용하는 방법에 대해 알아보겠다.

 필자는 Spring Boot 프로젝트가 모두 구성되어있다고 가정하고 그 위에 Swagger를 적용하겠다. 필요한 독자는 연결문서를 참고하기 바란다.

 먼저 Gradle에 의존성을 추가한다.
  
```groovy
dependencies {
    //...
    
    // Swagger / OpenAPI
	implementation 'org.springdoc:springdoc-openapi-ui:1.6.9'  
	implementation 'org.springdoc:springdoc-openapi-data-rest:1.6.9'
}

```

| 라이브러리 명                     | 기능                                  |
| --------------------------- | ----------------------------------- |
| springdoc-openapi           | API 문서를 브라우저에서 시각적으로 확인             |
| springdoc-openapi-data-rest | REST API End point를 확인하여 자동으로 문서 생성 |
| springdoc-openapi-security  | 보안설정을 openAPI 문서에 통합                |

 의존성을 추가했다면 Swagger 설정을 적용해보자
  
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

 설정 적용이 완료되면 WAS 실행 후 **\<ip\>:\<port\>/swagger-ui.html** 페이지에 접속한다. 이 상태만으로도 API 정보를 확인 할 수 있지만, 각 API 별 부가 설명이나 Parameter, Response에 대한 설명을 보강 할 수 있다. 
{: .notice}  
  
```java
@RestController  
@RequestMapping("/test")  
@Tag(name = "테스트 API", description = "Response 가 정상적으로 생성되는지 Test 하는 API")  
public class TestController {  
  
    @GetMapping("/string")  
    @Operation(summary = "String Response 테스트", description = "String Response가 정상적으로 생성되는지 확인")  
    public String testString() {  
        return "test";  
    }  
  
    @GetMapping("/json")  
    @Operation(summary = "Json Response 테스트", description = "Json Response가 정상적으로 생성되는지 확인")  
    public TestResponse getUserInfo() {  
        return new TestResponse("홍길동", "010-3333-3333");  
    }  
  
    @PostMapping("/json/withbody")  
    @Operation(summary = "요청 메서드에 Body 데이터가 있을 때, Json Response 테스트", description = "요청 메서드에 Body 데이터가 있을 때, Json Response 정상적으로 생성되는지 확인")  
    @ApiResponses(  
            {  
                    @ApiResponse(responseCode = "200", description = "정상 처리 완료"),  
                    @ApiResponse(responseCode = "400", description = "비 정상적인 Param")  
            }    )  
    public TestResponse getEchoUserInfo(@Parameter(description = "Json Body 데이터", required = true) @RequestBody TestRequest request) {  
        return new TestResponse(request.getName(), request.getRegistrationNumber());  
    }  
}
```
  
![image](../../assets/images/SwaggerUI.png)

 위 이미지는 각 어노테이션과 설정들이 Swagger UI의 어떤 부분에 해당하는지에 대한 설명이다.

 Swagger 문서에 노출되길 원하지 않는 API 경우 **@Hidden** Annotation을 적용하여 숨길 수 있다.
  
```java
@Hidden  
@GetMapping("/string")  
@Operation(summary = "String Response 테스트", description = "String Response가 정상적으로 생성되는지 확인")  
public String testString() {  
    return "test";  
}
```

 Response 객체에 정보를 추가하고 싶다면 **@Schema** Annotation을 사용한다.
  
```java
@Schema(description = "테스트 응답")  
public class TestResponse {  
    @Schema(description = "고객명", example = "홍길동")  
    String name;  
    @Schema(description = "고객 주민등록번호", example = "333333-3333333")  
    String registrationNumber;  
}
```

---
  
# 연결문서
- [Swagger](../../servercommon/servercommon-Swagger)
- [SpringBoot-Project](../../springboot/springboot-SpringBoot-Project)