---
title : "@Ignore"
excerpt : "@Ignore"
toc : true
toc_sticky : true
toc_label : "@Ignore"
categories:
- Test
tags:
- [Spring, Annotation, Test]
last_modified_at: 2023-11-07T08:00:00-10:00:00
---
  
---
  
## Artifact
- junit
  
## 역할
- 메소드는 남겨두되 테스트에서 제외할 항목 명시
  
## 사용법
  
```java
@Ignore  
private void writeLog(String logMessage){  
    System.out.println(logMessage);  
}
```

---
  
# 연결문서
