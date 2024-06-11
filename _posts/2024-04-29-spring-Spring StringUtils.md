---
title : "Spring StringUtils"
excerpt : "Spring StringUtils"
toc : true
toc_sticky : true
toc_label : "Spring StringUtils"
categories:
- Spring
tags:
- [Spring, 미완료]
last_modified_at: 2024-04-29T08:00:00-10:00:00
---
  
---
  
## 정의
> **StringUtils란**  
>
> springframework.util 에서 제공하는 문자열 처리 Util Class 
{: .notice--info}  
  
## Static Methods

| Method명     | 기능                                   |
| ----------- | ------------------------------------ |
| inEmpty()   | 문자열이 null이거나 비어있는지 체크                |
| hasLength() | 문자열이 null이 아니고 길이가 있는지 체크            |
| hasText()   | 문자열이 null이 아니고 길이가 있으며, 공백문자가 아닌지 체크 |
이외에도 다양한 Static Methods 가 있지만 이번 글에서는 위 3가지만 다루겠다.
  
## 사용법
Gradle (Short) 형식으로 build.gradle 파일에 의존성을 설정해준다.
  
```groovy
implementation 'org.springframework:spring-core:6.1.6'
```

각 메서드 별 사용 예시를 보도록 하자.
string 데이터 중 유의미한 데이터는 null이 아니고 공백문자가 없는 데이터 일 것이다. 이런 데이터를 확인하는 **hasText()** method부터 살펴보자.
  
```java
public static BooleanExpression stringUpperLikeIfExist(StringPath entityString, String emptableString) {  
    return StringUtils.hasText(emptableString) ? entityString.upper().like(emptiableString) : null;  
}
```
emptableString 값이 null이 아니며 공백문자가 없는지 확인하고, 내용이 있다면 [BooleanExpression](../../jpa/jpa-BooleanExpression)을 반환하는 샘플 코드이다.
  
---
  
# 연결문서
- [Gradle](../../build/build-Gradle)
- [BooleanExpression](../../jpa/jpa-BooleanExpression)