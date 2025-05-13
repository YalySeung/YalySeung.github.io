---
title : "MapStruct"
excerpt : "MapStruct"
toc : true
toc_sticky : true
toc_label : "MapStruct"
categories:
- Spring
tags:
- [Java, Spring]
last_modified_at: 2025-03-24T08:00:00-10:00:00
---
  
---
  
> **MapStruct란?**  
>
>  MapStruct는 **Java 애플리케이션에서 DTO와 Entity 간 변환을 자동화해주는 컴파일 타임 매핑 프레임워크**이다. 
{: .notice--info}  

 MapStruct는 코드 작성 없이 인터페이스만 정의하면 자동으로 매핑 구현체를 생성해주기 때문에 **성능이 뛰어나고 유지보수가 용이**하다.
  
## 📌 주요 특징

- **컴파일 타임에 매핑 코드 생성 → 성능 우수**
- **명시적인 인터페이스 기반 매핑 → 가독성, 안정성 우수**
- **Lombok, Spring과 호환성 우수**
- **다양한 매핑 전략 제공 (필드명 자동 매핑, 수동 매핑 가능)**

---
  
# 사용 방법
  
## ✅ 의존성 추가 (Gradle 기준)
  
```groovy
dependencies {
    implementation 'org.mapstruct:mapstruct:1.5.5.Final'
    annotationProcessor 'org.mapstruct:mapstruct-processor:1.5.5.Final'
}
```

---
  
## ✅ 기본 매퍼 인터페이스 정의
  
```java
@Mapper(componentModel = "spring")
public interface UserMapper {

    UserDTO toDto(User user);

    User toEntity(UserDTO userDTO);
}
```

---
  
## ✅ DTO / Entity 클래스 예시
  
```java
public class UserDTO {
    private String name;
    private String email;
    // getter, setter
}

public class User {
    private String name;
    private String email;
    // getter, setter
}
```

---
  
## ✅ 사용 예시
  
```java
@Service
@RequiredArgsConstructor
public class UserService {
    private final UserMapper userMapper;

    public UserDTO getUserDto(User user) {
        return userMapper.toDto(user);
    }
}
```

---
  
# 📌 고급 기능
  
## 🎯 다른 필드명 매핑
  
```java
@Mapper
public interface UserMapper {
    @Mapping(source = "userName", target = "name")
    UserDTO toDto(User user);
}
```
  
## 🎯 날짜 포맷팅 매핑
  
```java
@Mapping(source = "createdAt", target = "createdDate", dateFormat = "yyyy-MM-dd")
```
  
## 🎯 중첩 객체 매핑
  
```java
@Mapping(source = "address.city", target = "city")
```

---
  
# 📌 장점과 단점
  
### ✅ 장점
- 성능이 우수한 컴파일 **타임 코드 생성 방식**
- **Entity ↔ DTO 매핑 코드 간결화**
- 에러 발생 시 컴파일 타임에 확인 가능
  
### ❌ 단점
- 초기 설정과 학습 필요
- 복잡한 매핑은 커스터마이징이 필요할 수 있음

---
  
# 연결 문서
- [DTO](../../servercommon/servercommon-DTO)
