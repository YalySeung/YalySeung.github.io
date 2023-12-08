---
title : "@BeforeClass, @AfterClass"
excerpt : "@BeforeClass, @AfterClass"
toc : true
toc_sticky : true
toc_label : "@BeforeClass, @AfterClass"
categories:
- Test
tags:
- [Spring, Annotation, Test]
last_modified_at: 2023-11-07T08:00:00-10:00:00
---

# 날짜 : 2023-11-07 12:04

# 태그 : #Spring #Annotation #Test
---

# 내용

## Artifact
- junit

## 역할
- 해당 클래스에서 한번만 수행되는 메소드에 적용

## 사용법
- public 접근 제한자 사용
- static 함수로 정의해야 한다.

```java
@BeforeClass  
public static void classSetup(){  
    System.out.println("테스트 클래스 초기화 시작");  
}  
  
@AfterClass  
public static void classTearDown(){  
    System.out.println("테스트 클래스 초기화 종료");  
}
```

---

# 연결문서
