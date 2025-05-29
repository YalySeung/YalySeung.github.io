---
title : "MessageQueue"
excerpt : "MessageQueue"
toc : true
toc_sticky : true
toc_label : "MessageQueue"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2025-05-06T08:00:00-10:00:00
---
  
---
  
## 📌 메시지 큐(Message Queue)란?

> **info**
>
> **메시지 큐(MQ)**는 애플리케이션 간 비동기 통신을 위한 메시지를 일시적으로 저장하고 전달하는 미들웨어 시스템이다. 
{: .notice--info}  

생산자(Producer)가 보낸 메시지를 큐에 저장한 뒤, 소비자(Consumer)가 메시지를 읽어 처리하는 구조로 동작한다.

---
  
## ✅ 메시지 큐의 필요성

- **비동기 처리**: 요청과 응답을 분리하여 병렬 처리 가능
- **시스템 decoupling**: 발신자와 수신자의 강한 결합을 줄임
- **버퍼링 및 트래픽 제어**: 순간적인 요청 폭주에 대한 안정성 제공
- **재시도 및 보장된 전달**: 메시지 손실 방지

---
  
## ✅ 주요 메시지 큐 솔루션 비교

| 항목 | Kafka | RabbitMQ | Amazon SQS | Redis Streams |
|------|-------|----------|------------|----------------|
| 설계 목적 | 로그/이벤트 스트리밍 | 일반 메시징 | 클라우드 메시징 | 경량 메시징 |
| 처리 방식 | Pull 기반 | Push 기반 | Pull 기반 | Pull 기반 |
| 메시지 순서 | 파티션 내 보장 | 큐 기준 보장 | 없음 (FIFO 옵션 있음) | 보장 |
| 성능 | 초고속 처리 | 낮음~중간 | 중간 | 중간 |
| 영속성 | 기본 제공 | 기본 제공 | 옵션 | 옵션 |
| 복잡도 | 높음 | 중간 | 낮음 | 낮음 |

---
  
## ✅ 구성 요소 (일반적 메시지 큐 구조)

- **Producer**: 메시지를 생성하고 큐로 전송
- **Queue / Topic**: 메시지를 저장하는 버퍼
- **Consumer**: 큐에서 메시지를 읽어 비즈니스 로직 수행
- **Broker**: MQ 서버 자체, 라우팅 및 전달 담당

---
  
## ✅ 메시지 처리 흐름

1. Producer가 메시지를 MQ에 전송
2. Broker가 메시지를 Queue에 저장
3. Consumer가 메시지를 비동기적으로 수신 또는 polling
4. 처리 완료 시 MQ는 메시지를 삭제 (또는 Ack 처리)

---
  
## ✅ Spring에서 사용하는 예시 (RabbitMQ)
  
### 의존성
  
```groovy
implementation 'org.springframework.boot:spring-boot-starter-amqp'
```
  
### 설정 (application.yml)
  
```yaml
spring:
  rabbitmq:
    host: localhost
    port: 5672
    username: guest
    password: guest
```
  
### Producer 예시
  
```java
@Autowired
private RabbitTemplate rabbitTemplate;

public void send(String queue, String message) {
    rabbitTemplate.convertAndSend(queue, message);
}
```
  
### Consumer 예시
  
```java
@RabbitListener(queues = "myQueue")
public void receive(String message) {
    System.out.println("Received: " + message);
}
```

---
  
## ✅ 메시지 큐 사용 사례

- 결제 승인 요청 → 승인 처리 시스템
- 이메일/알림 비동기 전송
- 주문 처리 및 재고 관리
- 로그 비동기 수집
- IoT 센서 데이터 수집

---
  
# 연결 문서
- [kafka](../../servercommon/servercommon-kafka)
