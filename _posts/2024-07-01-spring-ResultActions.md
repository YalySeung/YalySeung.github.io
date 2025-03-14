---
title : "ResultActions"
excerpt : "ResultActions"
toc : true
toc_sticky : true
toc_label : "ResultActions"
categories:
- Spring
tags:
- [Spring]
last_modified_at: 2024-07-01T08:00:00-10:00:00
---
  
---
  
> **ResultActions란?**  
>
>  Spring MVC 테스트에서 `MockMvc`의 실행 결과를 검증하고 처리하는 객체이다. 
{: .notice--info}  

  `ResultActions`는 **MockMvc를 통해 수행된 요청의 결과를 확인하고 검증하는 데 사용된다.**
  
## 주요 메서드
  
| 메서드명               | 설명                                      |
| ------------------ | --------------------------------------- |
| andExpect()       | 응답 상태 코드, JSON 응답 값 등을 검증할 때 사용 |
| andDo()           | 디버깅을 위해 로그를 출력할 때 사용           |
| andReturn()       | 수행된 요청의 결과를 반환할 때 사용           |
  
## 사용법
  
### 1️⃣ 기본적인 `ResultActions` 활용 예제
  
```java
mockMvc.perform(get("/api/test"))
       .andExpect(status().isOk())
       .andExpect(jsonPath("$.message").value("Success"))
       .andDo(print());
```
  
## 장점과 단점
  
### ✅ 장점
- **Spring MVC 컨트롤러의 테스트를 체계적으로 수행 가능**  
- **JSON 응답을 쉽게 검증할 수 있음**  
  
### ❌ 단점
- **복잡한 테스트 케이스에서는 코드 가독성이 떨어질 수 있음**  
- **Hamcrest와 함께 사용하지 않으면 검증이 제한될 수 있음**  

---
  
# 연결문서
- [MockMVC](../../spring/spring-MockMVC)
