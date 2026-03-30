---
title : "JsonString Antipattern"
excerpt : "JsonString Antipattern"
toc : true
toc_sticky : true
toc_label : "JsonString Antipattern"
categories:
- ServerCommon
tags:
- [ServerCommon, Backend]
last_modified_at: 2026-03-11T08:00:00-10:00:00
---
  
---
  
## 개요

 JSON API 설계에서 `value` 필드를 **JSON String** 형태로 전달하는 방식은 단기적으로 구현이 쉬워 보이지만, 장기적으로는 설계 품질과 운영 안정성을 크게 떨어뜨리는 대표적인 **API Anti‑Pattern**이다.

 이 문서에서는 **설계 관점 / 운영 관점**에서 왜 JSON String 방식이 문제가 되는지 정리한다.

---
  
## 1️⃣ 타입 의미가 깨진다 (API 계약 위반)

 `value: String` 은 계약상 **문자열 타입**이다.  
 그런데 여기에 JSON을 문자열로 넣으면 실제 데이터는 **Object 또는 List**인데 겉으로는 String이 된다.
  
```json
{
  "value": "[{\"text\":\"10000\",\"confidence\":0.98}]"
}
```

 정리

| 항목 | 의미 |
|-----|-----|
| 스키마 | string |
| 실제 의미 | object / array |

 즉 **계약(Schema)과 의미(Domain)가 불일치**하게 된다.

---
  
## 2️⃣ 이중 직렬화 / 역직렬화 발생 (복잡도 증가)

 정상 JSON 구조

 서버  
 - 객체 → JSON 직렬화 (1번)

 클라이언트  
 - JSON → 객체 파싱 (1번)

 JSON String 구조

 서버  
 - 객체 → JSON String 직렬화 (1번)  
 - 전체 응답 JSON 직렬화 (2번)

 클라이언트  
 - 전체 JSON 파싱 (1번)  
 - value 문자열 다시 JSON.parse() (2번)

 결과

 - 파싱 단계 증가
 - 실패 지점 증가
 - 디버깅 난이도 상승

---
  
## 3️⃣ Validation / Swagger 문서화 무력화

 정상 JSON 구조라면

 - 필수 필드 검증
 - 타입 검증
 - 범위 검증

 JSON String 구조라면

```
value : string
```

 서버는 단순 문자열로만 인식한다.

---
  
## 4️⃣ 프론트 타입 안정성 붕괴

 React + TypeScript 기준

 정상 구조
  
```ts
value: Candidate[]
```

 JSON String 구조
  
```ts
value: string
JSON.parse(value)
```

 결과적으로 **방어 코드가 전체 코드에 퍼지게 된다**.

---
  
## 5️⃣ 확장 시 하위호환 문제

 초기 구조
  
```json
"value": "[\"A\",\"B\"]"
```

 확장
  
```json
"value": "[{\"text\":\"A\",\"confidence\":0.95}]"
```

 기존 파싱 코드가 깨질 가능성이 높다.

---
  
## 6️⃣ 로깅 / 보안 / 마스킹 문제

 JSON 구조라면

 - 특정 필드만 마스킹 가능

 JSON String 구조라면

 - 문자열 내부 파싱 필요
 - 마스킹 누락 위험 증가

---
  
## 결론

 > **JSON String 방식은 구조 설계를 미루는 선택이다**.

---
  
## 현실적인 타협안
  
```json
{
  "value": "대표값",
  "candidates": ["후보1","후보2"]
}
```

 기존 호환성과 확장성을 동시에 확보할 수 있다.

---
  
# 연결문서
- [Swagger](../../servercommon/servercommon-Swagger)
