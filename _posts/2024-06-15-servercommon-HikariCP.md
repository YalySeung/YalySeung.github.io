---
title : "HikariCP"
excerpt : "HikariCP"
toc : true
toc_sticky : true
toc_label : "HikariCP"
categories:
- ServerCommon
tags:
- [SpringBoot, JPA, Database]
last_modified_at: 2024-06-15T08:00:00-10:00:00
---
  
---
  
> **HikariCP란?**  
>
>  HikariCP는 **고성능 JDBC 커넥션 풀 라이브러리**로, 빠른 속도와 낮은 리소스 사용량을 자랑한다. 
{: .notice--info}  

  Spring Boot에서는 기본적으로 HikariCP를 데이터베이스 커넥션 풀로 사용하며, **커넥션 풀을 효율적으로 관리하여 성능을 최적화한다.**  
  
## 📌 HikariCP의 특징
- **빠른 성능** → 기존 커넥션 풀보다 속도가 빠름 (BoneCP, C3P0 대비)  
- **낮은 메모리 사용량** → 최소한의 리소스를 활용  
- **Spring Boot 기본 커넥션 풀** → 추가 설정 없이 사용 가능  
- **JDBC 4+ 및 JDK 8+ 지원**  
  
## 📌 Spring Boot에서 HikariCP 설정하기
  
### 1️⃣ Gradle 의존성 추가 (Spring Boot 사용 시 기본 포함됨)
  
```groovy
dependencies {
    implementation 'com.zaxxer:HikariCP:5.0.1'
}
```
  
### 2️⃣ `application.properties`에서 HikariCP 설정
  
```properties
  
# 데이터베이스 연결 설정
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
spring.datasource.username=root
spring.datasource.password=secret
  
# HikariCP 설정
spring.datasource.hikari.minimum-idle=5
spring.datasource.hikari.maximum-pool-size=20
spring.datasource.hikari.idle-timeout=30000
spring.datasource.hikari.max-lifetime=1800000
spring.datasource.hikari.connection-timeout=30000
spring.datasource.hikari.auto-commit=true
```
  
### 3️⃣ `application.yml`에서 HikariCP 설정
  
```yaml
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/mydb
    username: root
    password: secret
    hikari:
      minimum-idle: 5
      maximum-pool-size: 20
      idle-timeout: 30000
      max-lifetime: 1800000
      connection-timeout: 30000
      auto-commit: true
```
  
## 📌 HikariCP 주요 설정 값
  
| 설정 값 | 설명 |
|---------|------|
| `minimum-idle` | 최소 유지할 커넥션 개수 (기본값: `10`) |
| `maximum-pool-size` | 최대 커넥션 풀 크기 (기본값: `10`) |
| `idle-timeout` | 커넥션이 유휴 상태일 경우 제거되는 시간 (기본값: `600000ms`) |
| `max-lifetime` | 커넥션이 살아있을 수 있는 최대 시간 (기본값: `1800000ms`) |
| `connection-timeout` | 커넥션을 얻기 위해 기다리는 최대 시간 (기본값: `30000ms`) |
| `auto-commit` | 커넥션 반환 시 자동 커밋 여부 (기본값: `true`) |
  
## 📌 HikariCP를 직접 Java Configuration으로 설정
  
```java
import com.zaxxer.hikari.HikariConfig;
import com.zaxxer.hikari.HikariDataSource;
import javax.sql.DataSource;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class DataSourceConfig {

    @Bean
    public DataSource dataSource() {
        HikariConfig hikariConfig = new HikariConfig();
        hikariConfig.setJdbcUrl("jdbc:mysql://localhost:3306/mydb");
        hikariConfig.setUsername("root");
        hikariConfig.setPassword("secret");
        hikariConfig.setMaximumPoolSize(20);
        hikariConfig.setMinimumIdle(5);
        hikariConfig.setIdleTimeout(30000);
        hikariConfig.setMaxLifetime(1800000);
        hikariConfig.setConnectionTimeout(30000);
        hikariConfig.setAutoCommit(true);

        return new HikariDataSource(hikariConfig);
    }
}
```
  
## 📌 HikariCP의 장점과 단점
  
### ✅ 장점
- **빠른 커넥션 풀 성능**  
- **Spring Boot 기본 내장, 추가 설정 불필요**  
- **메모리 사용량이 적고, 설정이 간단**  
  
### ❌ 단점
- **커넥션 풀 크기 설정을 잘못하면 성능 저하 발생 가능**  
- **대규모 트래픽 환경에서는 추가적인 튜닝이 필요**  

---
  
# 연결문서
