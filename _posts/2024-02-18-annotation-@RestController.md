---
title : "@RestController"
excerpt : "@RestController"
toc : true
toc_sticky : true
toc_label : "@RestController"
categories:
- Annotation
tags:
- [Spring, Annotation, RESTAPI]
last_modified_at: 2024-02-18T08:00:00-10:00:00
---
  
---
  
## Artifact
- spring-context
  
## 역할
- [@Controller](../../annotation/annotation-@Controller) + [@ResponseBody](../../annotation/annotation-@ResponseBody)
- **Json Response를 반환**
  
## 사용법
  
```java
@RestController  
@RequestMapping("/authentication")  
public class AuthenticationController {
	...
}
```

---
  
# 연결문서
- [@Controller](../../annotation/annotation-@Controller)