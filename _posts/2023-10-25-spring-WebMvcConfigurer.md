---
title : "WebMvcConfigurer"
excerpt : "WebMvcConfigurer"
toc : true
toc_sticky : true
toc_label : "WebMvcConfigurer"
categories:
- Spring
tags:
- [Spring, Interface]
last_modified_at: 2023-10-25T08:00:00-10:00:00
---
  
---
  
## WebMvcConfigurer란
- [Boiler Plate](../../cleancode/cleancode-Boiler-Plate)코드 없이 요구사항에 맞게 프레임워크를 조정할 수 있게 해준다.
- [@EnableWebMvc](../../annotation/annotation-@EnableWebMvc) 를 통해 활성화된 Web MVC 애플리케이션의 구성정보 커스터마이징을 돕는다.
  
## Gradle 설정
  
```groovy
dependencies {
	implementation 'org.springframework:spring-webmvc:5.3.8'
}
```
  
## 용도
  
### 인터셉터 등록
- request를 핸들링 하기 전,후 처리가 필요할 때 커스텀 인터셉터를 구성한다.
  
```java
@Configuration  
@EnableWebMvc  
@ComponentScan(basePackages = "org.infinity.server.controller.api")
public class MvcConfig implements WebMvcConfigurer {

    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(new MyInterceptor());
    }
}
```
  
### 뷰 리졸버
- 컨트롤러에서 반환된 뷰 이름이 실제 뷰 오브젝트로 변환되는 과정을 정의
  
```java
@Override
public void configureViewResolvers(ViewResolverRegistry registry) {
    InternalResourceViewResolver resolver = new InternalResourceViewResolver();
    resolver.setPrefix("/WEB-INF/views/");
    resolver.setSuffix(".jsp");
    registry.viewResolver(resolver);
}
```

> **memo**
>
> [@EnableWebMvc](../../annotation/annotation-@EnableWebMvc) Annotation과 함께 적용해야 한다. 
{: .notice}  
  
### 리소스 핸들링
- javascript, Css, images 와 같은 정적 리소스를 제어
- 리소스의 위치를 설정할 수 있다.
  
```java
@Override
public void addResourceHandlers(ResourceHandlerRegistry registry) {
    registry.addResourceHandler("/assets/**")  
        .addResourceLocations("classpath:/static/assets/");  
	registry.addResourceHandler("/static/**")  
        .addResourceLocations("classpath:/static/");
}
```

> **memo**
>
> ResourceLocation은 폴더구조상의 경로
> ResourceHandler는 request 요청상의 경로이다 
{: .notice}  

> **example**
>
> http://localhost:8080/assets/my.js  이렇게 request가 들어왔다고 가정하면 classpath:/static/assets/ 경로에서 .js파일을 찾을 것이다. 
{: .notice}  
  
### Exception 핸들링
- Contoller 밖으로  Throw된 exception을 처리하고 동작방식 재정의
  
```java
@Override  
public void extendHandlerExceptionResolvers(List<HandlerExceptionResolver> resolvers) {   
{: .notice}  
    resolvers.add(new MyHandlerExceptionResolver());  
}
```
  
### 메세지 변환
- message converter를 추가하여 JSON, XML 과 같은 형식의 데이터를 읽고 쓸수 있도록 메시지 변환
  
```java
@Override
public void extendMessageConverters(List<HttpMessageConverter<?>> converters) { 
{: .notice}  
    converters.add(new MyCustomMessageConverter());
}
```
  
### Path Matching 
  
```java
@Override
public void configurePathMatch(PathMatchConfigurer configurer) {
    configurer.setUseTrailingSlashMatch(true);
}
```
  
### Content Negotiation
  
```java
@Override
public void configureContentNegotiation(ContentNegotiationConfigurer configurer) {
    configurer.favorPathExtension(false)
              .favorParameter(true)
              .parameterName("mediaType")
              .ignoreAcceptHeader(true)
              .useRegisteredExtensionsOnly(false)
              .defaultContentType(MediaType.APPLICATION_JSON)
              .mediaType("xml", MediaType.APPLICATION_XML);
}
```
  
### CORS Configuration
- 다른 도메인에 의해 접근되어야 할 때 필요한 CORS 규칙 정의
  
```java
@Override
public void addCorsMappings(CorsRegistry registry) {
    registry.addMapping("/**")
            .allowedOrigins("http://allowed-origin.com")
            .allowedMethods("GET", "POST")
            .allowCredentials(true);
}
```

---
  
# 연결문서
- [DispatcherServlet](../../spring/spring-DispatcherServlet)
- [MessageConverter](../../spring/spring-MessageConverter)
- [WebApplicationInitializer](../../spring/spring-WebApplicationInitializer)