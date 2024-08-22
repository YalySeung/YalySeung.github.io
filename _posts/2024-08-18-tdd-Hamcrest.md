---
title : "Hamcrest"
excerpt : "Hamcrest"
toc : true
toc_sticky : true
toc_label : "Hamcrest"
categories:
- TDD
tags:
- [TDD, UnitTest, java]
last_modified_at: 2024-08-18T08:00:00-10:00:00
---
  
---
  
 이 글에서는 Hamcrest 라이브러리에 대해 알아보도록 하겠다.

> **Hamcrest란?**  
>
> JUnit 기반의 기반의 단위테스트에서 사용할 수 있는 Assertion Framework 이다. 
{: .notice--info}  

 Hamcrest는 다양한 Matcher를 제공하여 객체의 속성이나 상태를 명확하고 직관적으로 검증할 수 있도록 돕는다.

 Hamcrest 라이브러리를 사용하기 위해서는 Spring의 Test 라이브러리와 Hamcrest 를 프로젝트 의존성에 추가해야 한다.
  
```groovy
testImplementation 'org.hamcrest:hamcrest:2.2'
testImplementation 'org.springframework:spring-test:5.3.8'
```
  
## Hamcrest를 사용하는 이유
 Hamcrest를 사용하는 이유는
 
 첫째, Hamcrest는 **테스트의 의도를 명확하게 표현**할 수 있는 문법을 제공한다. 
  
```java
// Hamcrest 사용 전 (JUnit의 기본 assertion)
assertEquals(5, value);

// Hamcrest 사용 후
assertThat(value, is(5));
```

 위 검증 코드를 살펴보면 Hamcrest를 사용한 코드는 마치 영어 문장처럼 읽기 쉽게 느껴진다.

 둘째, **유연한 Matcher를 제공**한다.

 Hamcrest는 기본적인 동등성 비교뿐만 아니라, 컬렉션 크기, 문자열 포함 여부, 객체 속성 등의 다양한 조건을 검증 할 수 있는 Matcher를 제공한다.
  
```java
// 예시: 리스트의 크기 확인
assertThat(list, hasSize(3));

// 예시: 문자열이 특정 단어를 포함하는지 확인
assertThat("Hello, World!", containsString("World"));
```

 셋째, Hamcrest의 Matcher는 조합이 가능하기 때문에 **복잡한 검증이 가능**하다.
  
```java
// 리스트가 비어 있지 않고, 특정 값을 포함하는지 확인
assertThat(list, allOf(not(empty()), hasItem("expectedValue")));
```

 넷째, 테스트 실패 시 더 이해하기 쉬운 메시지를 제공한다.
  
```java
// 실패 시
assertThat(value, is(5)); // Expected: is <5> but: was <4> 
{: .notice}  
```

 끝으로, Hamcrest는 테스트 코드에서 비교나 조건 검증을 매처로 캡슐화하여, 이후 리팩토링 시 테스트 코드가 더 안정적이고 유지보수하기 쉬워진다.

---
  
# 연결문서
