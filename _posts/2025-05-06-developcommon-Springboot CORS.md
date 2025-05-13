---
title : "Springboot CORS"
excerpt : "Springboot CORS"
toc : true
toc_sticky : true
toc_label : "Springboot CORS"
categories:
- DevelopCommon
tags:
- [SpringSecurity, SpringBoot]
last_modified_at: 2025-05-06T08:00:00-10:00:00
---
  
---
  
## 📌 보안 설정 파일 – `SecurityConfig.java`

Spring Security에서 인증, 인가, CORS 설정을 구성한 보안 설정 파일이다.
  
### ✅ 주요 기능 요약

- 특정 경로(`/api/photos/**`) 인증 필요
- 그 외 요청은 모두 허용
- Form 로그인 방식 사용 (`successHandler`, `failureHandler` 지정)
- 사용자 정의 UserService를 `userDetailsService`로 등록
- CORS 허용 설정

---
  
## 📌 SecurityFilterChain 설정
  
```java
@Bean
public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
    http.cors().and()
        .csrf().disable()
        .authorizeRequests()
        .antMatchers("/api/**").authenticated()
        .anyRequest().permitAll()
        .and()
        .formLogin()
        .successHandler((req, res, auth) -> res.setStatus(HttpServletResponse.SC_OK))
        .failureHandler((req, res, e) -> res.setStatus(HttpServletResponse.SC_UNAUTHORIZED))
        .and()
        .userDetailsService(userService);

    return http.build();
}
```
  
### ✳️ 설명

- `.cors()` : 커스텀 CORS 정책 적용
- `.csrf().disable()` : CSRF 보호 비활성화
- `.antMatchers("/api/**").authenticated()` : API는 인증 필요
- `.formLogin()` : 기본 로그인 폼 사용
- `.successHandler`, `.failureHandler` : 로그인 성공/실패 시 상태 코드 반환 (`200`, `401`)
- `.userDetailsService(userService)` : 커스텀 `UserService`로 사용자 정보 로드

---
  
## 📌 CORS Configuration 설정
  
```java
@Bean
public CorsConfigurationSource corsConfigurationSource() {
    CorsConfiguration config = new CorsConfiguration();
    config.setAllowedOriginPatterns(List.of("http://localhost:5173"));
    config.setAllowedMethods(List.of("GET", "POST", "PUT", "DELETE", "OPTIONS"));
    config.setAllowedHeaders(List.of("*"));
    config.setAllowCredentials(true);

    UrlBasedCorsConfigurationSource source = new UrlBasedCorsConfigurationSource();
    source.registerCorsConfiguration("/**", config);
    return source;
}
```
  
### ✳️ 설명

- `setAllowedOriginPatterns` : CORS 요청 허용 도메인 설정 (`localhost:5173`)
- `setAllowCredentials(true)` : 세션 쿠키 포함 허용
- 모든 경로(`/`)에 대해 설정 적용

---
  
## 📎 보충 개념

| 항목 | 설명 |
|------|------|
| SecurityFilterChain | Spring Security HTTP 보안 설정 핵심 구성 |
| Form Login | Spring Security 기본 로그인 방식 |
| UserDetailsService | 사용자 정보 로딩 서비스 |
| CORS | 외부 Origin에서의 요청 허용을 위한 설정 |
| SuccessHandler | 로그인 성공 후 동작 지정 |
| FailureHandler | 로그인 실패 시 동작 지정 |

---
  
# 연결 문서
- [SpringSecurity](../../spring/spring-SpringSecurity)
- [CORS](../../servercommon/servercommon-CORS)