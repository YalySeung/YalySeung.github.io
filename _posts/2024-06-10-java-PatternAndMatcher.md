---
title : "PatternAndMatcher"
excerpt : "PatternAndMatcher"
toc : true
toc_sticky : true
toc_label : "PatternAndMatcher"
categories:
- java
tags:
- [java]
last_modified_at: 2024-06-10T08:00:00-10:00:00
---
  
---
  
> **Pattern Class**  
>
> 정규식 패턴을 정의하는 클래스로, 한 번 컴파일 된 정규식을 나타내며, 여러번 재사용 할 수 있다. 
{: .notice--info}  

 Pattern Class를 사용하기 위한 주요 메서드를 살펴보자.
  
```java
//정규식 문쟈열 정의
String regex = "(\\d{4})(?:\\\\(\\d{1,2}))?(?:\\\\(\\d{1,2}))?";  
//패턴 생성
Pattern pattern = Pattern.compile(regex);
//입력 문자열과, 정규식을 매칭하는 Matcher 객체 생성
Matcher matcher = pattern.matcher(inputString);
```

> **Matcher Class**  
>
> Matcher Class는 Pattern 객체와 입력 문자열을 연결하여 실제 매칭 작업을 수행하는 클래스이다. 
{: .notice--info}  

 Matcher Class를 사용하기 위한 주요 메서드를 살펴보자.
  
```java
//부분 문자열 검색
if (matcher.find()){  
	//검색된 문자열의 그룹에서 값 가져오기
    String year = matcher.group(1);  
    String month = matcher.group(2);  
    String day = matcher.group(3);
}

// 전체 문자열 검색
if (matcher.matches()){  
	...
}

```
 검색해온 결과에서 **grouping 이 필요하다면 matcher.group 메서드를 사용**해서 가져온다.

---
  
# 연결문서
- [Regular Expression](../../expression/expression-Regular-Expression)