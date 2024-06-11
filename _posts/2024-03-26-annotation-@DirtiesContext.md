---
title : "@DirtiesContext"
excerpt : "@DirtiesContext"
toc : true
toc_sticky : true
toc_label : "@DirtiesContext"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2024-03-26T08:00:00-10:00:00
---
  
---
  
## Artifact
- Spring-test
  
## 역할
- 테스트시, TestCase간 Context 를 공유하여 발생하는 문제 해결
- 테스트 종료시, 테스트 프레임워크의 캐시를 제거하고 닫음
- classMode 에 설정한 시점에 따라 Context를 재생성
  
## 사용법
  
```java
@RunWith(SpringJUnit4ClassRunner.class)  
@ContextConfiguration(classes = RpaViewConfiguration.class)  
@Transactional  
@DirtiesContext(classMode = DirtiesContext.ClassMode.AFTER_CLASS)  
public class ViewTestBase {  
    @Test  
    public void dummyTest(){ 
	    fail(); 
    }  
    ...
}
```
  
### classMode
- dirty 시점 설정

| classMode               | 시점                     |
| ----------------------- | ---------------------- |
| BEFORE_CLASS            | Test Class 생성 전        |
| BEFORE_EACH_TEST_METHOD | 각 Test Method 실행 전     |
| AFTER_EACH_TEST_METHOD  | 각 Test Method 실행 후     |
| AFTER_CLASS             | Test Class 모든 메서드 종료 후 |

---
  
# 연결문서
- [@Test](../../test/test-@Test)
- [@RunWith](../../test/test-@RunWith)