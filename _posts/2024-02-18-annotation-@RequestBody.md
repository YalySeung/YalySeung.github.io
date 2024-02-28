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

# 날짜 : 2024-02-18 14:40

# 태그 : #Spring #Annotation
---

# 내용

## Artifact
- spring-web

## 역할
- HttpMessageConverter를 사용하여 Request 본문을  java객체로 Conversion 한다.

## 사용법

```java
@PostMapping(value = "/add")  
public ResponseEntity<UserAddResponse> addUser(@RequestBody @Valid UserAddForm userAddForm, BindingResult bindingResult) {  
    ...
}
```

---

# 연결문서
- [@Controller](../../annotation/annotation-@Controller)
- [@ResponseBody](../../annotation/annotation-@ResponseBody)