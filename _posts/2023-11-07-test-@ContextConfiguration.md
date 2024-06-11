---
title : "@ContextConfiguration"
excerpt : "@ContextConfiguration"
toc : true
toc_sticky : true
toc_label : "@ContextConfiguration"
categories:
- Test
tags:
- [Spring, Annotation, Test]
last_modified_at: 2023-11-07T08:00:00-10:00:00
---
  
---
  
## Artifact
- spring-test
  
## 역할
- 자동으로 만들어줄 ApplicationContext 설정 파일 위치를 지정
  
## 사용법
  
```java
@RunWith(SpringJUnit4ClassRunner.class)  
@ContextConfiguration(classes = RpaApiConfiguration.class)  
public class ScheduleTest {
	...
}
```
  
### ContextConfigutaion 속성
  
#### location
- applicationContext.xml 파일 경로 설정
  
#### classes
- class 형태의 ApplicationContext 설정

---
  
# 연결문서
- [@RunWith](../../test/test-@RunWith)