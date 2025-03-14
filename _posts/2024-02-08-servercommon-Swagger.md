---
title : "Swagger"
excerpt : "Swagger"
toc : true
toc_sticky : true
toc_label : "Swagger"
categories:
- ServerCommon
tags:
- [ServerCommon, BackEnd]
last_modified_at: 2024-02-08T08:00:00-10:00:00
---
  
---
  
> **Swagger란?**  
>
>  Web API 문서화를 위한 도구이다. 
{: .notice--info}  

  Backend 개발을 하며, 구조를 잘 잡고 소스코드를 잘 짜는 것도 중요하지만, Client 개발자와의 소통도 매우 중요하다.  

  전통적인 개발자들은 Excel에 API의 EndPoint별로 필요한 데이터와 응답 데이터를 직접 작성했다. 모듈이 수정될 때, 지속적으로 이 문서를 관리하지 않으면, **문서와 소스코드의 정보가 불일치**하는 문제가 생긴다. 그렇다고 **매번 문서를 갱신하는 것도 일이다**.  

  이런 문제를 해결하기 위해 Swagger를 도입했다. Swagger는 소스코드에 Annotation을 작성하여 관리하므로, **소스코드와 문서가 동기화 상태를 유지한다**. 또한 Swagger에서 기본 제공하는 UI 템플릿이 있어, Excel보다는 **가독성이 높다**. 부가적으로 직접 **API를 호출해볼 수 있는 기능**까지 가지고 있다.  
  
## Library 추가
  
```groovy
compile 'io.springfox:springfox-swagger-ui:2.9.2' 
compile 'io.springfox:springfox-swagger2:2.9.2'
```
  
## Swagger 설정

> **caution**
>
> `/swagger-ui.html` 리소스가 정상적으로 보이려면 `/v2/api-docs` 리소스가 정상적인 JSON 형태로 보여져야 한다. 
{: .notice--info}  
  
### 1️⃣ Configuration 설정
- `@Configuration`, `@EnableSwagger2` 두 개 Annotation 적용  
- `Docket`을 Bean으로 등록하고 Swagger 관련 설정 적용  
  
```java
@Configuration  
@EnableSwagger2  
@EnableWebMvc  
@EnableAspectJAutoProxy  
@ComponentScan(basePackages = {"sample.mysample"}, useDefaultFilters = false,  
        includeFilters = {@Filter(type = FilterType.ANNOTATION, value = {Controller.class, RestController.class})})  
public class RpaApiWebMvcConfiguration extends WebMvcConfigurerAdapter {  

	@Override  
	public void configureMessageConverters(List<HttpMessageConverter<?>> converters) {  
		converters.addAll(MessageConverterFactory.createMessageConverters());  
	}

    @Override  
    public void addViewControllers(ViewControllerRegistry registry) {  
        registry.addViewController("/swagger")  
                .setViewName("forward:/swagger-ui/index.html");  
    }  

    @Override  
    public void addResourceHandlers(ResourceHandlerRegistry registry) {  
        registry.addResourceHandler("/swagger-ui/**")  
                .addResourceLocations("classpath:/META-INF/resources/webjars/springfox-swagger-ui/")  
                .resourceChain(false);  
    }  

    @Bean  
    public Docket api() {  
        return new Docket(DocumentationType.SWAGGER_2)  
                .select()  
                .apis(RequestHandlerSelectors.any())  
                .paths(PathSelectors.any())  
                .build();  
    }  
}
```

> **tip**
>
> `configureMessageConverters` 함수 내의 Converter에 Swagger API JSON을 직렬화할 수 있는 Converter를 추가해야 한다. 
{: .notice--info}  
  
```java
public class MessageConverterFactory {  
    public static List<HttpMessageConverter<?>> createMessageConverters() {  
        return Arrays.asList(createGsonHttpMessageConverter());  
    }  

    public static GsonHttpMessageConverter createGsonHttpMessageConverter() { 
        Gson gson = new GsonBuilder()  
                .registerTypeAdapter(Json.class, new GsonSpringfoxJsonSerializer())  
                .create();  

        GsonHttpMessageConverter converter = new GsonHttpMessageConverter();  
        converter.setGson(gson);  
        converter.setSupportedMediaTypes(Arrays.asList(MediaType.APPLICATION_JSON_UTF8, MediaType.APPLICATION_JSON));  
        return converter;  
    }  
}

public class GsonSpringfoxJsonSerializer implements JsonSerializer<Json> {  
    @Override  
    public JsonElement serialize(Json json, Type type, JsonSerializationContext context) {  
        return JsonParser.parseString(json.value());  
    }  
}
```
  
## 주요 Swagger Annotations
  
### 2️⃣ API 정보 설정 (`@Api`)
- Swagger UI에서 API 정보를 명시
  
### 3️⃣ 엔드포인트 설명 (`@ApiOperation`)
  
```java
@ApiOperation(value = "사용자 정보 조회", notes = "사용자 정보를 반환하는 API")
@GetMapping("/user/info")
@ResponseBody
public UserDTO getUserList(String userId) {
	return userService.getUserInfo(userId);
}
```
  
### 4️⃣ 응답 정보 명시 (`@ApiResponses`)
  
```java
@PostMapping("/name")  
@ApiOperation(value = "사용자 이름을 가져온다")  
@ApiResponses(value = {  
        @ApiResponse(code = 1400, message = "사용자가 없습니다."),
        @ApiResponse(code = 1401, message = "사용자 정보 조회에 실패했습니다.")    
})  
public ResponseEntity<UserResponse> getUserName(  
        @ApiParam(value = "사용자 순번")  
        @RequestBody(required = true) @Valid Integer userSequence) {  
    ...
}
```
  
### 5️⃣ API 호출에 필요한 Parameter 정보 (`@ApiImplicitParam`)
  
```java
@ApiImplicitParam(name = "userId", value = "사용자 ID", required = true, dataType = "string", paramType = "query")
```
  
### 6️⃣ 모델 정보 (`@ApiModel`, `@ApiModelProperty`)
  
```java
@ApiModel(description = "사용자 정보 DTO")
public class UserDTO {
    
    @ApiModelProperty(value = "사용자 ID", example = "12345")
    private String userId;

    @ApiModelProperty(value = "사용자 이름", example = "홍길동")
    private String userName;
}
```

---
  
# 연결문서
