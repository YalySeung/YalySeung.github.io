---
title : "SSL"
excerpt : "SSL"
toc : true
toc_sticky : true
toc_label : "SSL"
categories:
- DevelopCommon
tags:
- [ServerCommon]
last_modified_at: 2023-12-12T08:00:00-10:00:00
---

# 날짜 : 2023-12-12 14:04

# 태그 : #ServerCommon
---

# 내용

## 정의
> SSL 이란?
> Secure Socket Layer
> 암호화 기반 인터넷 보안 프로토콜

## 특징
  
![image](./../../assets/images/../../assets/Images/SSLOperation.png)
- 높은 수준의 개인정보 보호 제공을 위해 웹에서 전송되는 데이터를 암호화
- 두 통신 장치 사이에 handshake 인증 프로세스로 ID를 확인
- 데이터 무결성 제공을 위해 데이터에 디지털 서명하여 데이터가 의도된 수신자에게 도착하기 전에 조작되지 않았음을 증명

## SSL 인증서

### 종류

| 종류        | 설명                                                                       |
|:----------- |:-------------------------------------------------------------------------- |
| 단일 도메인 | 단 하나의 도메인에 적용                                                    |
| 와일드 카드 | 단일 도메인 같은 단 하나의 도메인에 적용되지만 도메인의 하위 도메인도 포함 |
| 멀티 도메인 | 관련되지 않은 다수의 도메인에 적용 가능                                    |

---

# 연결문서
