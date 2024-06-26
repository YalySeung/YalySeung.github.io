---
title : "SpringMVC test"
excerpt : "SpringMVC test"
toc : true
toc_sticky : true
toc_label : "SpringMVC test"
categories:
- TDD
tags:
- [Spring, CleanCode, Test, TDD, 환경]
last_modified_at: 2023-11-07T08:00:00-10:00:00
---
  
---
  
## build.gradle
  
```groovy
dependencies {  
	...
    testImplementation 'org.springframework:spring-test:5.3.22'  
    testImplementation 'junit:junit:4.12'  
}  
  
test {  
    useJUnitPlatform()  
}
```
  
## Test
- [테스트 플로우](../../test/test-Junit-Test-Flow)
  
```java
@RunWith(SpringJUnit4ClassRunner.class)  
@ContextConfiguration(classes = ResourceManager.class)  
public class TestResourceManager {  
  
    @Test  
    public void TDDTest(){  
        ResourceManager rm = new ResourceManager();  
        Resource resource = rm.getResource("test.html");  
        System.out.println("resource : " + resource.getFilename());  
        Assert.notNull(resource);  
    }  
}

```
  
## Annotations
  
```dataview
table without id
file.link as SpringTestAnnotation
from #Spring and #Annotation and #Test 
where file != this.file
```

---
  
# 연결문서
- [Gradle](../../build/build-Gradle)
- [Junit Test Flow](../../test/test-Junit-Test-Flow)
- [TDD-Naming](../../tdd/tdd-TDD-Naming)