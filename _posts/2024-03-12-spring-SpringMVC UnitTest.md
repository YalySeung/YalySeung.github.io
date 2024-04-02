---
title : "SpringMVC UnitTest"
excerpt : "SpringMVC UnitTest"
toc : true
toc_sticky : true
toc_label : "SpringMVC UnitTest"
categories:
- Spring
tags:
- [Spring, UnitTest]
last_modified_at: 2024-03-12T08:00:00-10:00:00
---

# 날짜 : 2024-03-12 23:18

# 태그 : #Spring #UnitTest
---

# 내용

## SpringMVC UnitTest 환경 구성

### build.gradle

```groovy
dependencies {  
	...
    testImplementation 'org.springframework:spring-test:5.3.8'  
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.8.1'  
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine:5.8.1'  
}
```

### TestClass

```java
@ExtendWith(SpringExtension.class)  
@WebAppConfiguration  
@ContextConfiguration(classes = {APIConfiguration.class})  
class ApiTestControllerTest {
	...
}
```

> **tip**
>
> Junit4 에서는 @ExtendWith(SpringExtension.class) 대신에 @RunWith(SpringJUnit4ClassRunner.class) 를 사용한다.
{: .notice--primary}

---

# 연결문서
- [@WebAppConfiguration](../../test/test-@WebAppConfiguration)
- [@ContextConfiguration](../../test/test-@ContextConfiguration)