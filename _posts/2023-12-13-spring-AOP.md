---
title : "AOP"
excerpt : "AOP"
toc : true
toc_sticky : true
toc_label : "AOP"
categories:
- Spring
tags:
- [Spring, AOP]
last_modified_at: 2023-12-13T08:00:00-10:00:00
---

# 날짜 : 2023-12-13 16:51

# 태그 : #Spring #AOP 
---

# 내용

## 정의
>  AOP란?
> Aspect Oriented Programming(관점 지향 프로그래밍)
> 어떤 로직을 기준으로 핵심적인 관점, 부가적인 관점으로 나누고 그 기준을 각각 모듈화하는 관점 지향 프로그래밍 방법

## 목적
  
![image](../../assets/images/AOPConcept.png)
- 위와 같이 소스코드상에서 다른 부분에 계속 반복하여 사용하는 코드들을 Aspect로 모듈화
- 핵심적인 비즈니스 로직에서 분리하여 재사용

## 주요개념

| 용어      | 설명                                                                    |
| --------- |:----------------------------------------------------------------------- |
| Aspect    | 모듈화된 관심사, 주로 부가기능을 모듈화                                 |
| Target    | Aspect를 적용하는 곳, Advice의 대상이 되는 객체 (Class, Method)                                    |
| Advice    | 실질적으로 어떤일을 할지 정의한 구현체                                    |
| Advisor   | Spring AOP에서만 사용되는 용어, Advice + PointCut 한쌍                      |
| JoinPoint | Adivce가 적용될 위치, 메서드 자체(메서드 진입점, 생성자 호출 시점, 필드값 획득시 등) |
| PointCut  | JoinPoint의 상세 스펙을 정의                                            |
| Weaving   | PointCut으로 설정한 타겟의 Join Point 에 Advice를 적용하는 것           |
| AOP프록시 | AOP 기능을 구현하기 위해 만든 프록시 객체                               |

## 적용시점

### Compile 시점
- java 컴파일러를 통한 .class 생성 시점에 부가기능 추가
- 모든 지점에 적용 가능
- AspectJ 컴파일러 사용

### Class Loading 시점
- JVM 내부 Class Loader에 .class 파일을 보관하기 전 부가기능 추가
- 모든 지점에 적용 가능

### Runtime 시점
- **스프링에서 사용하는 방식**
- Application이 실행 된 후 동작하는 런타임 방식
- 실제 코드는 그대로 유지되며, Proxy를 통해 부가 기능 적용
- Proxy는 메서드 오버라이딩 방식으로 동작하기때문에 메서드에만 적용 가능
- 구현이 쉽다.

---

# 연결문서
- [@Aspect](../../aop/AOP-@Aspect)
- [Pointcut Designator](../../spring/Spring-Pointcut-Designator)