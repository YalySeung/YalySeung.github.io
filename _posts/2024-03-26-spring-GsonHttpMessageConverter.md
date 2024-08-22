---
title : "GsonHttpMessageConverter"
excerpt : "GsonHttpMessageConverter"
toc : true
toc_sticky : true
toc_label : "GsonHttpMessageConverter"
categories:
- Spring
tags:
- [Spring]
last_modified_at: 2024-03-26T08:00:00-10:00:00
---
  
---
  
## 정의
> **GsonHttpMessageConverter 란**  
>
> Spring MVC 에서 Json Data를 처리하는데 사용되는 HTTP MessageConverter 중 하나 
{: .notice--info}  
  
## 역할
- Java 객체를 JSON 형식으로 변환하여 HTTP Response Body에 포함시킴
- HTTP Request Body에 포함된 Json Data를 Java 객체로 변환하여 Controller에 전달
  
## 적용
  
### WebMvcConfigurer 를 사용한 기본 설정
  
```java
@Configuration  
@EnableWebMvc  
@ComponentScan(basePackages = "org.infinity.server.controller.api")
public class APIConfiguration implements WebMvcConfigurer {  
	...
	
    @Override  
    public void configureMessageConverters(List<HttpMessageConverter<?>> converters) {  
        Gson gson = new GsonBuilder().create();
  
        GsonHttpMessageConverter converter = new GsonHttpMessageConverter(gson);  
        converters.add(converter);  
    }  
}
```
  
### GsonHttpMessageConverter에 Custom Class 등록
  
#### 1. JsonSerializer<>를 구현하는 CustomSerializer 추가
  
```java
public class LocalDateSerializer implements JsonSerializer<LocalDate> {  
    private static final DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd");  
  
    @Override  
    public JsonElement serialize(LocalDate localDate, Type type, JsonSerializationContext jsonSerializationContext) {  
        return new JsonPrimitive(formatter.format(localDate));  
    }  
}
```
  
#### 2. MessageConverter에 등록
  
```java
@Configuration  
@EnableWebMvc  
@ComponentScan(basePackages = "org.infinity.server.controller.api")
public class APIConfiguration implements WebMvcConfigurer {  
	...
	
    @Override  
    public void configureMessageConverters(List<HttpMessageConverter<?>> converters) {  
        Gson gson = new GsonBuilder()  
                .registerTypeAdapter(LocalDate.class, new LocalDateSerializer())  
                .create();  
  
        GsonHttpMessageConverter converter = new GsonHttpMessageConverter(gson);  
        converters.add(converter);  
    }  
}
```
  
#### 3. 타입에 따른 converter 등록
  
```java
public static GsonHttpMessageConverter createGsonHttpMessageConverter() {  
    Gson gson = new GsonBuilder()  
            .registerTypeAdapter(DateTime.class, new GsonDateTimeTypeAdapter())  
            .registerTypeAdapter(String.class, new GsonStringXssTypeAdapter())  
            .registerTypeAdapter(Json.class, new GsonSpringfoxJsonSerializer())  
            .create();  
	...
}
```

---
  
# 연결문서
- [WebMvcConfigurer](../../spring/spring-WebMvcConfigurer)
- [MessageConverter](../../spring/spring-MessageConverter)
- [@ResponseBody](../../annotation/annotation-@ResponseBody)
- [@Controller](../../annotation/annotation-@Controller)