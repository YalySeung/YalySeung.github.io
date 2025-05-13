---
title : "@Autowired"
excerpt : "@Autowired"
toc : true
toc_sticky : true
toc_label : "@Autowired"
categories:
- Annotation
tags:
- [Spring, Annotation, Autowired]
last_modified_at: 2025-03-24T08:00:00-10:00:00
---
  
---
  
> **`@Autowired` 어노테이션이란?**  
>
> `@Autowired`는 **Spring에서 의존성 주입(DI, Dependency Injection)을 자동으로 수행하도록 지원하는 어노테이션**이다. 
{: .notice--info}  

 `@Autowired`는 타입(Type)을 기준으로 Bean을 자동으로 연결하며, 동일한 타입의 Bean이 여러 개 존재할 경우 에러가 발생할 수 있다.

---
  
## 📌 주요 역할 및 특징

- **필요한 의존 객체의 타입에 해당하는 Bean을 자동으로 찾아 주입**
- **동일 타입 Bean이 여러 개 있을 경우 명시적으로 선택 필요 (`@Qualifier`)**
- **다양한 위치에 적용 가능 (생성자, Setter, 필드)**

---
  
## 📌 적용 가능한 대상

| 적용 위치  | 추천 정도 | 특징                          |
|-----------|-----------|-------------------------------|
| 생성자(Constructor) | ✅ 권장 | 불변성 및 명확한 의존 관계 표현 |
| Setter 메소드 | ⚠️ 주의 | 선택적 주입 또는 재주입 필요 시 사용 |
| 필드(Field) | ❌ 비권장 | 테스트 및 유지보수 어려움, 객체 오염 가능성 |

---
  
## 📌 의존성 주입 방식
  
### ✅ Constructor Injection (권장)

- **불변성 유지와 명확한 의존 관계를 제공**
  
```java
@Service
public class UserService {
    private final UserRepository userRepository;

    @Autowired
    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }
}
```

---
  
### ⚠️ Setter Injection

- **의존성 재주입 또는 선택적 주입이 가능**
  
```java
@Service
public class UserService {
    private UserRepository userRepository;

    @Autowired
    public void setUserRepository(UserRepository userRepository) {
        this.userRepository = userRepository;
    }
}
```

---
  
### ❌ Field Injection (비권장)

- **사용하기 쉽지만 객체 관리가 어렵고 테스트가 어려움**
  
```java
@Service
public class UserService {
    @Autowired
    private UserRepository userRepository;
}
```

---
  
## 📌 `@Qualifier`로 Bean 선택

동일 타입의 Bean이 여러 개 존재할 경우 명시적 선택을 위한 방법
  
```java
@Service
public class UserService {
    private final UserRepository userRepository;

    @Autowired
    public UserService(@Qualifier("jdbcUserRepository") UserRepository userRepository) {
        this.userRepository = userRepository;
    }
}
```

---
  
## 📌 장점과 단점
  
### ✅ 장점
- **편리한 자동 주입**
- **코드의 간결성 유지**
- **의존 관계 자동 관리**
  
### ❌ 단점
- **암묵적인 의존 관계로 인해 유지보수 및 테스트 어려움 가능**
- **Field Injection 사용 시 단일 책임 원칙 위반 가능성**

---
  
## 📌 연결 문서
- [@Qualifier](../../annotation/annotation-@Qualifier)
