---
title : "ValidationConstraint"
excerpt : "ValidationConstraint"
toc : true
toc_sticky : true
toc_label : "ValidationConstraint"
categories:
- Spring
tags:
- [Spring]
last_modified_at: 2025-03-24T08:00:00-10:00:00
---
  
---
  
> **Bean Validation에서 제공하는 대표적인 제약 조건 애노테이션들**  
>
>  `@NotNull`, `@NotEmpty`, `@NotBlank`는 **값의 존재 여부를 검증**할 때 사용되는 애노테이션이다. 
{: .notice--info}  

 이 세 가지는 유사하지만 적용 대상과 동작 방식에 차이가 있다.
  
## 📌 각 애노테이션의 비교

| 애노테이션 | null 허용 | 빈 문자열 허용 | 공백 문자열 허용 | 컬렉션 검사 | 주요 대상 |
|------------|-----------|----------------|------------------|-------------|-----------|
| `@NotNull` | ❌ 불가    | ✅ 허용         | ✅ 허용           | ❌           | 모든 타입  |
| `@NotEmpty`| ❌ 불가    | ❌ 불가         | ✅ 허용           | ✅           | String, 배열, 컬렉션 |
| `@NotBlank`| ❌ 불가    | ❌ 불가         | ❌ 불가           | ❌           | 문자열만 (String) |

> **note**
>
> - `@NotNull`: 값이 반드시 존재해야 함  
> - `@NotEmpty`: null이 아니고 비어있지 않아야 함 (길이 또는 크기 > 0)  
> - `@NotBlank`: null이 아니고 비어있지 않으며 공백만 있는 문자열도 허용하지 않음 
{: .notice--info}  
  
## 📌 사용 예시
  
```java
public class UserRequest {

    @NotNull
    private String id; // 반드시 값이 존재해야 함

    @NotEmpty
    private List<String> tags; // null 또는 빈 리스트 허용하지 않음

    @NotBlank
    private String name; // " " 공백도 허용하지 않음
}
```
  
## 📌 메시지 커스터마이징 예시
  
```java
@NotBlank(message = "이름은 필수 입력 항목입니다.")
private String name;

@NotEmpty(message = "최소 하나의 태그가 필요합니다.")
private List<String> tags;

@NotNull(message = "ID는 null일 수 없습니다.")
private Long id;
```
  
## 📌 언제 어떤 애노테이션을 써야 할까?

- `@NotNull` → 필드가 null이 아니면 통과. 문자열이든 컬렉션이든 null 여부만 확인할 때 사용  
- `@NotEmpty` → null 뿐 아니라 비어있지 않아야 할 때. 컬렉션, 배열, 문자열에서 사용  
- `@NotBlank` → 문자열만 사용 가능. 공백 문자열도 허용하지 않아야 할 때

---
  
# 연결문서