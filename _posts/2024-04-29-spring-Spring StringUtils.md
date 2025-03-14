---
title : "Spring StringUtils"
excerpt : "Spring StringUtils"
toc : true
toc_sticky : true
toc_label : "Spring StringUtils"
categories:
- Spring
tags:
- [Spring]
last_modified_at: 2024-04-29T08:00:00-10:00:00
---
  
---
  
## 정의
> **StringUtils란?**  
>
>  `springframework.util`에서 제공하는 문자열 처리 Util Class이다. 
{: .notice--info}  

  `StringUtils`는 **Spring에서 문자열을 보다 편리하게 다룰 수 있도록 제공되는 유틸리티 클래스**이다.
  
## Static Methods
  
| Method명     | 기능                                   |
| ----------- | ------------------------------------ |
| **isEmpty()**   | 문자열이 `null`이거나 비어있는지 체크 |
| **hasLength()** | 문자열이 `null`이 아니고 길이가 있는지 체크 |
| **hasText()**   | 문자열이 `null`이 아니고 길이가 있으며, 공백 문자가 아닌지 체크 |
  
## 사용법
  
### 1️⃣ Gradle 의존성 추가
  
```groovy
implementation 'org.springframework:spring-core:6.1.6'
```
  
### 2️⃣ `hasText()` 활용 예제
  `hasText()`는 문자열이 `null`이 아니고, 공백 문자가 포함되지 않은 경우 `true`를 반환한다.
  
```java
public static BooleanExpression stringUpperLikeIfExist(StringPath entityString, String emptableString) {  
    return StringUtils.hasText(emptableString) ? entityString.upper().like(emptableString) : null;  
}
```

  위 예제에서는 `emptableString` 값이 `null`이 아니며 공백 문자가 없는지 확인하고, 내용이 있다면 `BooleanExpression`을 반환한다.
  
## 장점과 단점
  
### ✅ 장점
- **NPE(Null Pointer Exception) 방지를 위한 유용한 메서드 제공**  
- **Spring에서 문자열 검증을 간편하게 수행 가능**  
  
### ❌ 단점
- **Java 기본 제공 메서드(`isEmpty()`, `isBlank()`)와 중복될 수 있음**  
- **Spring Core에 의존성이 필요**  

---
  
# 연결문서
- [Gradle](../../build/build-Gradle)
- [BooleanExpression](../../jpa/jpa-BooleanExpression)
