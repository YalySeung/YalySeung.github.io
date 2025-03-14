---
title : "@WebAppConfiguration"
excerpt : "@WebAppConfiguration"
toc : true
toc_sticky : true
toc_label : "@WebAppConfiguration"
categories:
- Test
tags:
- [Spring, Annotation, Test]
last_modified_at: 2024-03-12T08:00:00-10:00:00
---
  
---
  
> **`@WebAppConfiguration`이란?**  
>
>  Spring MVC 테스트에서 `WebApplicationContext`를 로드하기 위해 사용하는 어노테이션이다. 
{: .notice--info}  

  `@WebAppConfiguration`을 사용하면 **테스트 환경에서 실제 서블릿 컨텍스트를 로드하여 컨트롤러와 서비스 계층을 테스트할 수 있다.**  
  
## Artifact
- `org.springframework.test.context`
  
## 역할
- **Spring MVC의 `WebApplicationContext`를 설정하여 통합 테스트 환경 제공**  
- **`MockMvc`와 함께 사용하여 컨트롤러 테스트 가능**  
  
## 사용법
  
### 1️⃣ `@WebAppConfiguration` 적용 예제
  
```java
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.test.context.web.WebAppConfiguration;
import org.springframework.test.web.servlet.MockMvc;
import org.springframework.test.web.servlet.setup.MockMvcBuilders;
import org.springframework.web.context.WebApplicationContext;

import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.get;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.status;

@SpringBootTest
@WebAppConfiguration
public class WebAppTest {

    @Autowired
    private WebApplicationContext wac;

    private MockMvc mockMvc;

    @BeforeEach
    void setup() {
        mockMvc = MockMvcBuilders.webAppContextSetup(wac).build();
    }

    @Test
    void testController() throws Exception {
        mockMvc.perform(get("/api/test"))
               .andExpect(status().isOk());
    }
}
```
  
## 장점과 단점
  
### ✅ 장점
- **Spring MVC 환경을 그대로 테스트 가능**  
- **`MockMvc`와 결합하여 컨트롤러 단위 테스트 수행**  
  
### ❌ 단점
- **테스트 실행 속도가 상대적으로 느림**  
- **Spring Boot 환경에서는 `@SpringBootTest`만으로 충분한 경우가 많음**  

---
  
# 연결문서
