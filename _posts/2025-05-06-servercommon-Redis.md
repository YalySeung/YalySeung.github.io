---
title : "Redis"
excerpt : "Redis"
toc : true
toc_sticky : true
toc_label : "Redis"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2025-05-06T08:00:00-10:00:00
---
  
---
  
## 📌 Redis란?

> **info**
>
> **Redis**(REmote DIctionary Server)는 인메모리 기반의 Key-Value 데이터 저장소이며, 초고속 읽기/쓰기 성능과 다양한 자료구조를 지원하는 NoSQL 데이터베이스이다. 
{: .notice--info}  

주로 **캐시(Cache)**, **세션 저장소(Session Store)**, **메시지 브로커(Pub/Sub)** 등으로 활용된다.

---
  
## ✅ Redis 특징

- **인메모리 저장소**: 데이터를 메모리에 저장하여 빠른 응답속도 제공
- **데이터 영속성**: 디스크에 Snapshot 또는 Append Only File로 백업 가능
- **다양한 자료구조**: String, List, Set, Sorted Set, Hash, Bitmap 등 지원
- **단일 스레드 기반의 고속 처리**
- **Replication, Cluster, Sentinel 기능으로 확장성 및 고가용성 제공**

---
  
## ✅ Redis 기본 자료구조

| 자료구조       | 설명                  | 예시                           |
| ---------- | ------------------- | ---------------------------- |
| String     | 기본 Key-Value 저장     | `"key" → "value"`            |
| List       | 삽입 순서가 유지되는 문자열 리스트 | `LPUSH queue A`              |
| Set        | 중복이 없는 문자열 집합       | `SADD tags java`             |
| Hash       | 필드-값 쌍으로 구성된 객체     | `HSET user:1 name "Alice"`   |
| Sorted Set | 정렬된 Set (점수 기반)     | `ZADD ranking 100 "player1"` |

---
  
## ✅ Spring Boot 설정 예시 (application.yml)
  
```yaml
spring:
  redis:
    host: localhost
    port: 6379
    password: yourpassword
```

---
  
## ✅ 의존성 (Gradle)
  
```groovy
implementation 'org.springframework.boot:spring-boot-starter-data-redis'
```

---
  
## ✅ RedisTemplate 사용 예시
  
```java
@Autowired
private RedisTemplate<String, String> redisTemplate;

public void saveData(String key, String value) {
    redisTemplate.opsForValue().set(key, value);
}

public String getData(String key) {
    return redisTemplate.opsForValue().get(key);
}
```

---
  
## ✅ 캐시로 사용 시 예시 (@Cacheable)
  
```java
@Cacheable(value = "users", key = "#id")
public User getUserById(Long id) {
    return userRepository.findById(id).orElse(null);
}
```

> **note**
>
> `@EnableCaching` 어노테이션을 `@SpringBootApplication` 또는 설정 클래스에 추가해야 캐시 기능이 활성화됨 
{: .notice--info}  

---
  
## ✅ Redis 주요 활용 사례

- 사용자 로그인 세션 저장
- JWT 토큰 블랙리스트 관리
- 실시간 랭킹 시스템
- 캐싱을 통한 DB 부하 감소
- Pub/Sub을 통한 채팅 시스템 구현

---
  
# 연결 문서
