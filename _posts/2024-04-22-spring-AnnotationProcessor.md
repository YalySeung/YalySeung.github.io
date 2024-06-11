---
title : "AnnotationProcessor"
excerpt : "AnnotationProcessor"
toc : true
toc_sticky : true
toc_label : "AnnotationProcessor"
categories:
- Spring
tags:
- [Spring]
last_modified_at: 2024-04-22T08:00:00-10:00:00
---
  
---
  
## 정의
> **AnnotationProcessor란?**  
>
> Java Compiler의 Compile 단계에서, 사용자가 정의한 Annotation 소스코드를 분석하고 처리하기 위해 사용하는 Hook 
{: .notice--info}  
  
## 역할
  
### Annotation 분석
- 주어진 소스코드나 클래스파일에서 Annotation을 찾아내고 분석
  
### Annotation을 이용한 코드 생성
- Annotation을 통해 소스코드의 생성 또는 변형을 수행
- 주로 리소스 파일이나 다른 소스 코드파일을 생성하는데 사용됨
  
### Compile 시점 검증
- Annotation을 사용하여 코드의 유효성을 검증하고 오류를 발견
- 특정한 규칙을 준수하지 않는 코드를 검출하여 경고나 오류 메시지를 출력
  
## IntelliJ에서 설정
- [Intellij](../../ide/ide-Intellij#annotationprocessor)

---
  
# 연결문서
- [Lombok](../../spring/spring-Lombok)
- [Intellij](../../ide/ide-Intellij#annotationprocessor)