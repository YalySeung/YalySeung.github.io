---
title : "SpringSecurity"
excerpt : "SpringSecurity"
toc : true
toc_sticky : true
toc_label : "SpringSecurity"
categories:
- Spring
tags:
- [Java, Spring]
last_modified_at: 2025-03-24T08:00:00-10:00:00
---
  
---
  
> **Spring Security란?**  
>
> Spring Security는 **Spring 기반 애플리케이션의 보안을 담당하는 하위 프레임워크**이다. 
{: .notice--info}  

 Spring Security는 인증(authentication)과 인가(authorization)를 효과적으로 처리하여 애플리케이션의 보안을 강화하는 역할을 수행한다.

---
  
## 📌 주요 특징
- **인증과 인가 기능의 통합 지원**
- **다양한 인증 방식 지원 (세션, JWT 등)**
- **Role 기반의 세부 권한 설정 가능**
- **다양한 보안 공격 대응 기능 제공 (CSRF, CORS 방지 등)**

---
  
## 📌 핵심 구조
  
### ✅ SecurityContextHolder
- 보안 주체의 세부 정보를 포함한 보안 컨텍스트를 관리
  
### ✅ SecurityContext
- 현재 인증된 사용자의 인증 정보(`Authentication`)를 저장하고 제공
  
### ✅ Authentication
- 현재 접근 주체의 정보를 담고 있으며 권한까지 관리
  
### ✅ AuthenticationProvider
- 실제 인증 로직 처리
- 인증 전 `Authentication` 객체를 받아 인증 완료된 객체 반환
  
### ✅ AuthenticationManager
- 인증 프로세스를 관리하고 `AuthenticationProvider`에 인증 작업 위임
  
### ✅ UserDetails
- 인증이 완료된 사용자 정보를 담는 객체

---
  
## 📌 간단 사용 예시
  
### 🎯 의존성 추가 (Gradle 기준)
  
```groovy
implementation 'org.springframework.boot:spring-boot-starter-security'
```
  
### 🎯 기본 보안 설정
  
```java
@Configuration
@EnableWebSecurity
public class SecurityConfig {

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        return http
            .authorizeHttpRequests(auth -> auth
                .requestMatchers("/admin/**").hasRole("ADMIN")
                .requestMatchers("/user/**").authenticated()
                .anyRequest().permitAll()
            )
            .formLogin(withDefaults())
            .build();
    }
}
```
  
### 🎯 UserDetailsService 구현
  
```java
@Service
public class CustomUserDetailsService implements UserDetailsService {
    
    private final UserRepository userRepository;

    public CustomUserDetailsService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }

    @Override
    public UserDetails loadUserByUsername(String username) throws UsernameNotFoundException {
        User user = userRepository.findByEmail(username)
                .orElseThrow(() -> new UsernameNotFoundException("User not found"));
        
        return new org.springframework.security.core.userdetails.User(
            user.getEmail(),
            user.getPassword(),
            Collections.singletonList(new SimpleGrantedAuthority(user.getRole()))
        );
    }
}
```

---
  
## 📌 세션(Session) 기반 인증 흐름

> **Spring Security에서 세션 기반 인증이란?**  
>
> 사용자가 로그인 후 세션에 인증 정보를 저장하고, 이후 요청마다 세션을 통해 인증 상태를 유지하는 방식이다. 
{: .notice--info}  

1. 사용자가 로그인하면 `Authentication` 객체가 생성되어 `SecurityContext`에 저장된다.
2. 이 `SecurityContext`는 `SecurityContextPersistenceFilter`를 통해 `HttpSession`에 저장된다.
3. 이후 요청에서는 `JSESSIONID` 쿠키를 통해 세션을 식별하고 인증 상태를 유지한다.
  
```java
// 인증 객체 저장 위치
SecurityContextHolder.getContext().getAuthentication();
```

---
  
## 📌 세션 유지 및 타임아웃 설정
  
### 🌐 application.properties에서 타임아웃 설정
  
```properties
server.servlet.session.timeout=30m
```

- 30분 동안 요청이 없으면 세션이 만료된다.
  
### 🧱 특정 API에만 세션 유지 적용
  
```java
@Configuration
@EnableWebSecurity
public class SecurityConfig {

    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
        return http
            .sessionManagement(session -> session
                .sessionCreationPolicy(SessionCreationPolicy.IF_REQUIRED)
            )
            .authorizeHttpRequests(auth -> auth
                .requestMatchers("/scan/**").authenticated()
                .anyRequest().permitAll()
            )
            .build();
    }
}
```

> **tip**
>
> `SessionCreationPolicy.IF_REQUIRED`는 필요할 때만 세션을 생성한다. 
{: .notice--info}  

---
  
## 📌 세션에 사용자 정보 저장하기
  
```java
@Override
public void onAuthenticationSuccess(HttpServletRequest request,
                                    HttpServletResponse response,
                                    Authentication authentication) throws IOException, ServletException {
    HttpSession session = request.getSession();
    CustomUserDetails userDetails = (CustomUserDetails) authentication.getPrincipal();
    session.setAttribute("empNo", userDetails.getEmpNo()); // 사번 저장
}
```

- 인증 성공 시 세션에 사번 등의 사용자 정보를 저장할 수 있다.

---
  
## 📌 Swagger 인증 예외 처리
  
```java
.antMatchers(
    "/v3/api-docs/**",
    "/swagger-ui/**",
    "/swagger-ui.html"
).permitAll()
```

- Swagger 요청은 인증 없이 접근 가능하도록 설정한다.

---
  
## 📌 JSESSIONID와 쿠키 주의점

- 세션 유지에는 브라우저가 쿠키(`JSESSIONID`)를 자동으로 전송하는 것이 필요하다.
- API 클라이언트(Postman, Swagger 등) 사용 시 쿠키 자동 전송 여부를 확인해야 한다.

---
  
# 연결 문서
- [인증과 인가](../../servercommon/servercommon-인증과-인가)
- [DTO](../../servercommon/servercommon-DTO)
- [@Entity](../../jpa/jpa-@Entity)
