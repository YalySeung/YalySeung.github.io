---
title : "Springboot GlobalException"
excerpt : "Springboot GlobalException"
toc : true
toc_sticky : true
toc_label : "Springboot GlobalException"
categories:
- SpringBoot
tags:
- [SpringBoot]
last_modified_at: 2024-11-27T08:00:00-10:00:00
---
  
---
  
> **Spring Boot에서 Global Exception 처리란?**  
>
>  컨트롤러 레벨에서 발생하는 예외를 전역적으로 처리하여 코드 중복을 방지하는 방법이다. 
{: .notice--info}  

  Spring Boot에서는 **`@ControllerAdvice`를 사용하여 전역적으로 예외를 처리할 수 있으며, 이를 통해 코드의 유지보수성을 높일 수 있다.**
  
## 전역 예외 처리 설정
  
### 1️⃣ `@ControllerAdvice`를 활용한 예제
  
```java
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.ControllerAdvice;
import org.springframework.web.bind.annotation.ExceptionHandler;
import org.springframework.web.bind.annotation.RestController;

@ControllerAdvice
@RestController
public class GlobalExceptionHandler {

    @ExceptionHandler(value = { IllegalArgumentException.class })
    public ResponseEntity<String> handleIllegalArgumentException(IllegalArgumentException ex) {
        return new ResponseEntity<>("Invalid input: " + ex.getMessage(), HttpStatus.BAD_REQUEST);
    }

    @ExceptionHandler(value = { NullPointerException.class })
    public ResponseEntity<String> handleNullPointerException(NullPointerException ex) {
        return new ResponseEntity<>("Unexpected error: " + ex.getMessage(), HttpStatus.INTERNAL_SERVER_ERROR);
    }

    @ExceptionHandler(value = { Exception.class })
    public ResponseEntity<String> handleGeneralException(Exception ex) {
        return new ResponseEntity<>("Error: " + ex.getMessage(), HttpStatus.INTERNAL_SERVER_ERROR);
    }
}
```
  
## 장점과 단점
  
### ✅ 장점
- **컨트롤러마다 `try-catch`를 작성할 필요 없이 예외를 중앙에서 처리 가능**  
- **예외 메시지를 일관되게 관리할 수 있어 유지보수성 향상**  
  
### ❌ 단점
- **전역 예외 처리만으로 해결되지 않는 경우가 있어, 특정 예외는 개별 처리 필요**  
- **예외 처리 로직이 복잡해질 경우 관리가 어려울 수 있음**  

---
  
# 연결문서
