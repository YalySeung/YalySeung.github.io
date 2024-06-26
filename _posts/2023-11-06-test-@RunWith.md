---
title : "@RunWith"
excerpt : "@RunWith"
toc : true
toc_sticky : true
toc_label : "@RunWith"
categories:
- Test
tags:
- [Spring, Annotation, Test]
last_modified_at: 2023-11-06T08:00:00-10:00:00
---
  
---
  
## Artifact
- junit4.x
  
## 역할
- JUnit 프레임워크의 테스트 실행 방법을 확장
- ApplicationContext를 만들고 관리하는 작업을 이동
  
## 사용법
  
```java
@RunWith(SpringJUnit4ClassRunner.class)  
@ContextConfiguration(classes = ResourceManager.class)  
public class TestResourceManager {  
    @Test  
    public void TDDTest(){  
        Assert.isNull(null);  
    }  
}
```

> **tip**
>
> DB 와 관련된 테스트라면, Class에 @Transactional 태그를 적용하여 DB에 영향이 가지 않도록 하자 
{: .notice--primary}  
  
### SpringJUnit4ClassRunner.class
- 컨테이너 모든 설정 정보를 가지고 있는 class

---
  
# 연결문서
- [TestDouble](../../tdd/tdd-TestDouble)
- [@Transactional](../../annotation/annotation-@Transactional)