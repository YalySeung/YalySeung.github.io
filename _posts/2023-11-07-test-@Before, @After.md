---
title : "@Before, @After"
excerpt : "@Before, @After"
toc : true
toc_sticky : true
toc_label : "@Before, @After"
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
- 테스트 메소드가 실행되기 전, 후로 항상 실행되는 메소드를 지정
- 공통으로 실행되어야 할 메소드에 적용
  
## 사용법
  
```java
@Before  
public void setup(){  
    System.out.println("테스트 시작");  
}  
  
@After  
public void tearDown(){  
    System.out.println("테스트 종료");  
}
```

---
  
# 연결문서
