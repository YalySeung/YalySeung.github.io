---
title : "Awaitility"
excerpt : "Awaitility"
toc : true
toc_sticky : true
toc_label : "Awaitility"
categories:
- Spring
tags:
- [Spring, UnitTest, Test]
last_modified_at: 2024-03-15T08:00:00-10:00:00
---
  
---
  
## 정의
> **Awaitility란?**  
>
> 비동기 코드의 단위테스트를 위한 Util 
{: .notice--info}  
  
## artifact
- org.awaitility
  
## 비동기 코드 Test Case
- 특정 시간 이내에 조건 만족 확인
- 특정 시간 이후에 조건 만족 확인
- 특정 시간동안 연속해서 조건 만족 확인
  
## Gradle
  
```groovy
dependencies {
	...
	testCompile "org.awaitility:awaitility:4.0.3"
}
```
  
## Methods
  
#### 특정 시간 시내에 조건 만족
  
```java
await().atMost(5, SECONDS).until(() -> {   
{: .notice}  
    return testMapper.insert(EXPECTED_OBJECT);    
});
```
  
#### 특정 시간 이후에 조건 만족
  
```java
await().atLeast(5, SECONDS).until(() -> {   
{: .notice}  
    return testMapper.insert(EXPECTED_OBJECT);  
});
```
  
#### 특정시간동안 연속해서 조건 만족
  
```java
await().during(2, SECONDS).atLeast(5, SECONDS).until(() -> {   
{: .notice}  
    return testMapper.insert(EXPECTED_OBJECT);  
});
```

---
  
# 연결문서
- [Gradle](../../build/build-Gradle)
- [@Test](../../test/test-@Test)
- [SpringMVC-test](../../tdd/tdd-SpringMVC-test)