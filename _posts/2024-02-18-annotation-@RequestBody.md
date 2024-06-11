---
title : "@RequestBody"
excerpt : "@RequestBody"
toc : true
toc_sticky : true
toc_label : "@RequestBody"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2024-02-18T08:00:00-10:00:00
---
  
---
  
## Artifact
- spring-web
  
## 역할
- HttpMessageConverter를 사용하여 Request 본문을  java객체로 Conversion 한다.
  
## 사용법
  
```java
@PostMapping(value = "/add")  
public ResponseEntity<UserAddResponse> addUser(@RequestBody @Valid UserAddForm userAddForm, BindingResult bindingResult) {   
{: .notice--primary}  
    ...
}
```

> **tip**
>
> @RequestBody Annotation만으로 Request에 담긴 json body 데이터를 Conversion 할 수 없다. Converter도 함께 설정해주어야 한다. 
{: .notice}  
  
```java
@Configuration  
@EnableWebMvc  
public class APIConfiguration implements WebMvcConfigurer {  
	@Override  
	public void configureMessageConverters(List<HttpMessageConverter<?>> converters) {   
{: .notice}  
	    GsonHttpMessageConverter converter = new GsonHttpMessageConverter();  
	    converters.add(converter);  
	}
}
```
  
```groovy
implementation 'com.google.code.gson:gson:2.8.8'
```

---
  
# 연결문서
- [@Controller](../../annotation/annotation-@Controller)
- [@ResponseBody](../../annotation/annotation-@ResponseBody)