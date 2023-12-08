---
title : "SpringMVC 구현"
excerpt : "SpringMVC 구현"
toc : true
toc_sticky : true
toc_label : "SpringMVC 구현"
categories:
- Spring
tags:
- [사이드프로젝트, BackEnd, Spring]
last_modified_at: 2023-09-17T08:00:00-10:00:00
---

# 날짜 : 2023-09-17 23:33

# 태그 : #사이드프로젝트 #BackEnd #Spring
---

# 내용

### 폴더 구조
![image](./../../assets/images/SpringMVCDirectoryStructure.png)

### build.gradle

```Groovy
apply plugin: 'war'  
apply plugin: 'java'  
  
group 'spring.sample'  
version '1.0-SNAPSHOT'  

webAppDirName = "src/main/webapp"

war {  
}  
  
repositories {  
    mavenCentral()  
}  
  
dependencies {  
    implementation 'org.springframework:spring-web:5.3.22'  
    implementation 'javax.servlet:javax.servlet-api:4.0.1'  
    implementation 'org.springframework:spring-webmvc:5.3.8'  
    implementation 'org.springframework:spring-context:5.3.22'  
  
//    implementation 'org.springframework:spring-core:5.3.22'  
//    implementation 'org.springframework:spring-context:5.3.22'  
  
    implementation 'log4j:log4j:1.2.17'  
  
    testImplementation 'org.springframework:spring-test:5.3.8'  
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.8.1'  
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine:5.8.1'  
}  
  
test {  
    useJUnitPlatform()  
}
```

- junit : 단위테스트
- log4j : 로깅
- spring-web : WebApplicationInitializer, DispatcherServlet, @RestController, @RequestMapping, @GetMapping
- spring-context : @ComponentScan, @Configuration
- javax.servlet : ServletRegistration

### WebApplicationInitializer

```JAVA
public class ApplicationInitializer implements WebApplicationInitializer {  
    @Override  
    public void onStartup(javax.servlet.ServletContext servletContext) throws ServletException {  
  
        AnnotationConfigWebApplicationContext context = new AnnotationConfigWebApplicationContext();  
        context.register(SampleConfiguration.class);  
  
        DispatcherServlet dispatcherServlet = new DispatcherServlet(context);  
  
        ServletRegistration.Dynamic dispatcher = servletContext.addServlet("dispatcher", dispatcherServlet);  
        dispatcher.addMapping("/");  
    }  
}
```

- DispatcherServlet 등록 필수!

### Configuration
- RESTAPI 설정

```JAVA
@Configuration  
@ComponentScan(basePackages = "spring.sample")  
public class SampleConfiguration {  
}
```

- Web설정

```java
public class SampleConfiguration implements WebMvcConfigurer {  
    @Override  
    public void configureViewResolvers(ViewResolverRegistry registry) {  
        InternalResourceViewResolver resolver = new InternalResourceViewResolver();  
        resolver.setPrefix("/WEB-INF/");  
        resolver.setSuffix(".jsp");  
        registry.viewResolver(resolver);  
    }  
}
```

### Test Controller

```java
@Controller  
@RequestMapping("/main")  
public class IndexWebContoller {  
    @GetMapping("")  
    public ModelAndView getMainPage(){  
        ModelAndView mv = new ModelAndView();  
        mv.setViewName("/index");  
        return mv;  
    }  
}
```

---

# 연결문서
- [WebMvcConfigurer](../../Spring/Spring-WebMvcConfigurer)

