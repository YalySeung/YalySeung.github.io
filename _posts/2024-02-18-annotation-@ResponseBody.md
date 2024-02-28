---
title : "@ResponseBody"
excerpt : "@ResponseBody"
toc : true
toc_sticky : true
toc_label : "@ResponseBody"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2024-02-18T08:00:00-10:00:00
---

# 날짜 : 2024-02-18 14:39

# 태그 : #Spring #Annotation
---

# 내용

## Artifact
- spring-web

## 역할
- response를 HTTP response의 body 부분에 그대로 전달

## 사용법

```java
@GetMapping("")  
@ResponseBody  
public String testString(){  
    return "test success";  
}
```

![image](../../assets/images/ResponseBodyResult.png)

---

# 연결문서
- [@Controller](../../annotation/annotation-@Controller)
- [@RequestBody](../../annotation/annotation-@RequestBody)