---
title : "Spring-classpath"
excerpt : "Spring-classpath"
toc : true
toc_sticky : true
toc_label : "Spring-classpath"
categories:
- Spring
tags:
- [Spring]
last_modified_at: 2023-11-06T08:00:00-10:00:00
---

# 날짜 : 2023-11-06 12:13

# 태그 : #Spring
---

# 내용

## classpath 란
- JVM이 프로그램을 실행할 때, class 파일을 찾는 기준 경로
- 경로를 지정하지 않으면 JVM이 위치한 경로에서만 class를 탐색

## intellij 에서 classpath 설정
  
![image](../../assets/images/IntellijClassPath.png)
- Source, Resoureses 에 포함된 경로는 모두 classpath에 해당한다.

## ClassPathResource
- ClassPath 에 있는 Resource를 가져오는 Class

```java
public Resource getResource(String relativePath) {  
    ClassPathResource resource = new ClassPathResource("/WEB-INF/");  
    return resource.createRelative(relativePath);  
}
```

---

# 연결문서
- [Intellij](../../ide/ide-Intellij)