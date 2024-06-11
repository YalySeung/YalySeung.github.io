---
title : "@Configuration"
excerpt : "@Configuration"
toc : true
toc_sticky : true
toc_label : "@Configuration"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2024-04-14T08:00:00-10:00:00
---
  
---
  
## Artifact
- org.springframework.context.annotation
  
## 역할
- 설정 Class를 명시하고, Bean으로 등록
- @Configuration이 적용되 Class는 [Singleton](../../designpattern/designpattern-Singleton) 생성됨
  
## 사용법
  
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

---
  
# 연결문서
- [Singleton](../../designpattern/designpattern-Singleton)