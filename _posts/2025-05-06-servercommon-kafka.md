---
title : "kafka"
excerpt : "kafka"
toc : true
toc_sticky : true
toc_label : "kafka"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2025-05-06T08:00:00-10:00:00
---
  
---
  
## 📌 Kafka란?

> **info**
>
> **Apache Kafka**는 고성능의 분산 메시지 스트리밍 플랫폼으로, 실시간 데이터 파이프라인과 스트리밍 애플리케이션에 사용된다. 
{: .notice--info}  

Kafka는 **Publisher(Producer)**와 **Subscriber(Consumer)** 간의 메시지를 중개하는 역할을 하며, 대용량 로그 처리 및 이벤트 기반 시스템에 적합하다.

---
  
## ✅ 주요 개념

| 용어                 | 설명                          |
| ------------------ | --------------------------- |
| **Broker**         | Kafka 서버로 메시지를 저장하고 관리하는 단위 |
| **Topic**          | 메시지를 구분하는 논리적 채널            |
| **Producer**       | 메시지를 Topic에 전송하는 클라이언트      |
| **Consumer**       | Topic에서 메시지를 읽는 클라이언트       |
| **Partition**      | Topic 내 데이터를 분산 저장하는 단위     |
| **Offset**         | 각 Partition 내 메시지의 고유 번호    |
| **Consumer Group** | 병렬 처리를 위한 Consumer 집합       |

---
  
## ✅ 동작 흐름

1. Producer가 특정 Topic에 메시지를 전송
2. 메시지는 Topic 내 Partition에 저장됨
3. Consumer는 해당 Topic을 구독하고 Partition에서 메시지를 읽음
4. Offset을 기준으로 메시지 소비 위치를 추적

---
  
## ✅ Kafka의 특징

- **분산 구조**: Broker 간 클러스터링을 통한 확장성
- **내결함성**: 복제 기능으로 데이터 유실 방지
- **고성능**: 수백 MB/s 처리 가능
- **내구성**: 디스크 기반 로그 저장
- **확장성**: Partition 단위 수평 확장 가능

---
  
## ✅ 기본 설정 예시 (application.yml)
  
```yaml
spring:
  kafka:
    bootstrap-servers: localhost:9092
    consumer:
      group-id: my-group
      auto-offset-reset: earliest
      key-deserializer: org.apache.kafka.common.serialization.StringDeserializer
      value-deserializer: org.apache.kafka.common.serialization.StringDeserializer
    producer:
      key-serializer: org.apache.kafka.common.serialization.StringSerializer
      value-serializer: org.apache.kafka.common.serialization.StringSerializer
```

---
  
## ✅ Producer 코드 예시
  
```java
@Autowired
private KafkaTemplate<String, String> kafkaTemplate;

public void send(String topic, String message) {
    kafkaTemplate.send(topic, message);
}
```

---
  
## ✅ Consumer 코드 예시
  
```java
@KafkaListener(topics = "my-topic", groupId = "my-group")
public void listen(String message) {
    System.out.println("Received: " + message);
}
```

---
  
## ✅ 사용 사례

- 실시간 로그 수집 (ELK 연동)
- 실시간 알림 시스템
- 마이크로서비스 간 이벤트 처리
- IoT 센서 데이터 수집

---
  
# 연결 문서