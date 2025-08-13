---
title : "AI OCR NPL"
excerpt : "AI OCR NPL"
toc : true
toc_sticky : true
toc_label : "AI OCR NPL"
categories:
- AI
tags:
- [AI, 딥러닝]
last_modified_at: 2025-07-04T08:00:00-10:00:00
---
  
---
  
## 개요
 이 문서에서는 OCR(광학 문자 인식) 및 NLP 관련 주요 아키텍처인 **CRAFT**, **TRBA**에 대해 정리하였다. 두 모델은 이미지 기반 문자인식에 사용되며, 주로 자연어 기반 시스템에서 사전 텍스트 인식 단계로 사용된다.

---
  
## 🧠 CRAFT (Character Region Awareness for Text detection)

> **CRAFT는 문자 단위의 위치 정보를 예측해 텍스트 영역을 탐지하는 모델이다.**  
> 
{: .notice--info}  

- 이미지 내에서 **문자 단위의 region map**과 **link map**을 추출
- Fully Convolutional Network 기반
- 연결된 문자들을 그룹핑하여 단어 단위 텍스트 박스를 형성
- 다국어 텍스트와 비정형 배치에 강인함
  
```plaintext
입력: 텍스트 이미지
출력: 글자 중심점 + 연결 관계 => 단어 단위 박스
```

> **example**
>
> Scene Text Detection, 문서 스캔 이미지 전처리 등에서 사용 
{: .notice--info}  

---
  
## 🧠 TRBA (TPS-ResNet-BiLSTM-Attention)

> **TRBA는 OCR의 텍스트 인식(Recognition)을 위한 아키텍처 구성 방식이다.**  
>
> 4단계 모듈로 이루어진 파이프라인 구조로, 기존 CRNN의 성능을 강화한 구조이다. 
{: .notice--info}  
  
### 📦 구성 단계

| 단계 | 모듈명 | 설명 |
|------|--------|------|
| 1 | TPS (Thin Plate Spline) | 입력 이미지 정규화 (왜곡 보정) |
| 2 | ResNet Feature Extractor | 이미지에서 특성 추출 |
| 3 | BiLSTM | 시퀀스 특성 추출 (왼쪽~오른쪽 문맥 고려) |
| 4 | Attention Decoder | 문자 시퀀스 생성 (유연한 길이 예측 가능) |
  
```plaintext
입력: 단어 영역 이미지
출력: 문자열 (예: "OpenAI")
```

---
  
## 활용 및 통합 예시

- `CRAFT`는 **텍스트 영역을 탐지**하고,  
- `TRBA`는 해당 영역에서 **문자열을 인식**하는데 사용됨
- 이 두 모델을 결합하여 End-to-End OCR Pipeline 구성 가능
- 사내 NLP 시스템에서 OCR 전처리 단계로 도입 가능

---
  
## 참고

- CRAFT: https://arxiv.org/abs/1904.01941  
- TRBA: https://arxiv.org/abs/1904.01906  
- 구현체: [https://github.com/clovaai/deep-text-recognition-benchmark](https://github.com/clovaai/deep-text-recognition-benchmark)

---
  
# 연결문서