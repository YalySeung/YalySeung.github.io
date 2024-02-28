---
title : "@Controller"
excerpt : "@Controller"
toc : true
toc_sticky : true
toc_label : "@Controller"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2024-02-18T08:00:00-10:00:00
---

# 날짜 : 2024-02-18 14:14

# 태그 : #Spring #Annotation
---

# 내용

## Artifact
- spring-context

## 역할
- SpringMVC에서 웹 요청을 처리하는데 사용
- **주로 view를 반환하는데 사용**

> **tip**
>
> @Controller를 Data를 반환하는데 사용하는 경우 @ResponseBody Annotation과 함께 사용해야 Json 형태로 데이터를 반환할 수 있다. 일반적으로 반환값은 ResponseEntity로 감싸서 반환한다.
{: .notice--info}

## 사용법

```java
@Controller  
@RequestMapping("/test")  
public class ApiTestController {  
    @GetMapping("")  
    @ResponseBody  
    public String testString(){  
        return "test success";  
    }  
}
```

---

# 연결문서
- [@RestController](../../annotation/annotation-@RestController)
- [@ResponseBody](../../annotation/annotation-@ResponseBody)