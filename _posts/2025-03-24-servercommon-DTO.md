---
title : "DTO"
excerpt : "DTO"
toc : true
toc_sticky : true
toc_label : "DTO"
categories:
- ServerCommon
tags:
- [ServerCommon, Spring, JPA]
last_modified_at: 2025-03-24T08:00:00-10:00:00
---
  
---
  
> **DTO란?**  
>
>  DTO(Data Transfer Object)는 **계층 간 데이터 교환을 위해 사용하는 객체**이다. 
{: .notice--info}  

  DTO는 Entity 객체와는 분리된 구조로, **데이터 표현에 최적화된 구조를 가지며** 클라이언트와의 통신, 화면 출력 등에 활용된다.
  
## 📌 DTO의 주요 목적
- **계층 간 데이터 전달을 명확하게 구분**
- **엔티티에 종속되지 않는 표현 전용 구조**
- **보안 및 API 응답 제어**
  
## 📌 DTO와 Entity의 차이점

| 항목    | Entity        | DTO           |
| ----- | ------------- | ------------- |
| 목적    | DB 테이블과 매핑    | 데이터 전달        |
| 포함 정보 | 전체 도메인 데이터    | 필요한 데이터만      |
| 위치    | 도메인 계층        | 프레젠테이션 계층     |
| 책임    | 비즈니스 로직 포함 가능 | 단순 전달 및 변환 역할 |
| 수정/변경 | 직접적으로 DB에 반영  | DB와 무관        |
  
## 주요 어노테이션 비교

| 어노테이션             | 전달 방식            | 주 사용 용도     | DTO 바인딩 | Bean Validation 적용      |
| ----------------- | ---------------- | ----------- | ------- | ----------------------- |
| `@RequestParam`   | 쿼리 파라미터, 폼 데이터   | 단일 값, 간단한 폼 | ❌       | ✅ (`@Validated`와 함께 사용) |
| `@RequestBody`    | JSON 등 HTTP Body | 복잡한 JSON 구조 | ✅       | ✅                       |
| `@ModelAttribute` | 쿼리 파라미터, 폼 데이터   | 폼 전체 객체 바인딩 | ✅       | ✅                       |
  
## 사용 예시
  
### ✅ `@RequestParam` 예시
  
```java
@GetMapping("/search")
public String search(@RequestParam String keyword) {
    return "검색어: " + keyword;
}
```
  
### ✅ `@RequestBody` 예시
  
```java
@PostMapping("/users")
public ResponseEntity<String> createUser(@RequestBody @Valid UserRequest request) {
    return ResponseEntity.ok("사용자 등록 완료: " + request.getName());
}
```
  
### ✅ `@ModelAttribute` 예시
  
```java
@PostMapping("/form")
public String submitForm(@ModelAttribute UserForm userForm) {
    return "제출 완료: " + userForm.getName();
}
```
  
## 📌 DTO 사용 예제
  
### 1️⃣ DTO 클래스 정의
  
```java
public class UserResponseDTO {
    private String name;
    private String email;

    public UserResponseDTO(String name, String email) {
        this.name = name;
        this.email = email;
    }

    // getter, setter 생략
}
```
  
### 2️⃣ Entity → DTO 변환 예시
  
```java
User user = userRepository.findById(1L).orElseThrow();
UserResponseDTO dto = new UserResponseDTO(user.getName(), user.getEmail());
```
  
## 📌 DTO 자동 매핑 도구

| 라이브러리 | 특징 |
|-----------|------|
| ModelMapper | 필드 이름 기반 자동 매핑 |
| MapStruct | 컴파일 타임 매핑, 성능 우수 |
| Orika | 속도와 유연성 모두 제공 |
  
## 📌 장점과 단점
  
### ✅ 장점
- **도메인 모델과 API 응답 구조 분리**  
- **불필요한 정보 노출 방지**  
- View 또는 API에 최적화된 구조 설계 가능  
  
### ❌ 단점
- **DTO 클래스가 많아질 경우 관리 비용 증가**  
- **Entity-DTO 간 변환 로직 필요**  

---
  
# 연결문서
- [@Entity](../../jpa/jpa-@Entity)
- [@Controller](../../annotation/annotation-@Controller)
