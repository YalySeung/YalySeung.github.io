---
title : "Swagger"
excerpt : "Swagger"
toc : true
toc_sticky : true
toc_label : "Swagger"
categories:
- ServerCommon
tags:
- [ServerCommon, 미완료]
last_modified_at: 2024-02-08T08:00:00-10:00:00
---

# 날짜 : 2024-02-08 13:33

# 태그 : #ServerCommon #미완료 
---

# 내용

## 정의
> **Swagger 란?**
>
> Web API 문서화를 위한 도구
{: .notice--info}

## 장점
- Web API 스펙이 변경되면, 문서도 같이 변경됨
- 문서 작성 시간을 줄여 협업의 효율성 증가

## library

```ruby
complie 'io.springfox:springfox-swagger-ui:2.9.2' 
compile 'io.springfox:springfox-swagger2:2.9.2'
```

## 설정

> **caution**
>
> /swagger-ui.html 리소스가 정상적으로 보이려면 /v2/api-docs 리소스가 정상적인 json 형태로 보여져야한다.
{: .notice--info}

### Configuration
- @Configuration , @EnableSwagger2 두개 Annotation 적용
- Docket 을 bean으로 등록하고, Swagger 관련 설정 적용

``` java
@Configuration  // 설정 파일 명시
@EnableSwagger2  // Swagger Annocation 적용
@EnableWebMvc  
@EnableAspectJAutoProxy  
@ComponentScan(basePackages = {"sample.mysample"}, useDefaultFilters = false,  
        includeFilters = {@Filter(type = FilterType.ANNOTATION, value = {Controller.class, RestController.class})})  
public class RpaApiWebMvcConfiguration extends WebMvcConfigurerAdapter {  
	...  
	@Override  
	public void configureMessageConverters(List<HttpMessageConverter<?>> converters) {  
		converters.addAll(MessageConverterFactory.createMessageConverters());  
	}

	// 리다이렉팅
    @Override  
    public void addViewControllers(ViewControllerRegistry registry) {  
        registry.addViewController("/swagger")  
                .setViewName("forward:/swagger-ui/index.html");  
    }  

	// Swagger UI 사용을 위한 리소스 접근 하용
    @Override  
    public void addResourceHandlers(ResourceHandlerRegistry registry) {  
        registry.addResourceHandler("/swagger-ui/**")  
                .addResourceLocations("classpath:/META-INF/resources/webjars/springfox-swagger-ui/")  
                .resourceChain(false);  
    }  

	// 기본 화면 설정
    @Bean  
    public Docket api(){  
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
> configureMessageConverters 함수내의 Converter에 Swagger API Json을 직렬화 할 수 있는 Converter를 추가해야한다.
{: .notice--info}

```java
public class MessageConverterFactory {  
  
    /**  
     * Create MessageConverters.     *     * @return {@link HttpMessageConverter} arrays  
     */    public static List<HttpMessageConverter<?>> createMessageConverters() {  
        return Arrays.asList(  
                createGsonHttpMessageConverter(),  
        );  
    }  
  
    /**  
     * Create GsonHttpMessageConverter.     *     * @return {@link GsonHttpMessageConverter}  
     */  
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

// 직렬화
public class GsonSpringfoxJsonSerializer implements JsonSerializer<Json> {  
    @Override  
    public JsonElement serialize(Json json, Type type, JsonSerializationContext context) {  
        return JsonParser.parseString(json.value());  
    }  
}
```

### Annotations

#### @Api
- SwaggerUI 의 API 정보를 명시

#### @ApiOperation
- endpoint 정보를 명시

```java
@ApiOperation(value = <Method 요약>, notes = <상세설명>)
@GetMapping("/user/info")
@ResponseBody
public UserDTO getUserList(String userId) {
	return userService.getUserInfo(userId);
}
```

#### @ApiResponses
- Response 정보를 명시

#### @ApiParam
- request param 정보를 명시

#### @ApiModel
- Model 정보를 명시

#### @ApiModelProperty
- Model 내의 Property 정보를 명시

#### @ApilmplicitParam
- API 호출에 필요한 Parameter 정보 명시

---

# 연결문서
