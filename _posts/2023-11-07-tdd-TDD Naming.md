---
title : "TDD Naming"
excerpt : "TDD Naming"
toc : true
toc_sticky : true
toc_label : "TDD Naming"
categories:
- TDD
tags:
- [Test, TDD, CleanCode]
last_modified_at: 2023-11-07T08:00:00-10:00:00
---
  
---
  
 이 글에서는 **TDD**에서 사용하는 **테스트 함수의 Naming 전략**에 대해서 살펴보겠다. Naiming 방법과 예시를 확인해보자.
  
## 메서드명_테스트상태_기대결과
 이 Naming 방법은 조건과 예상 결과를 메서드명으로 확인할 수 있다는 장점이 있지만, 코드 리팩토링으로 인한 메서드명 변경시, 테스트도 변경해야한다.
  
```java
isAdult_AgeLessThan18_False(){}
withdrawMoney_InvalidAccount_ExceptionThrown(){}
admitStudent_MissingMandatoryFields_FailToAdmit(){}
```
  
## 메서드명_기대결과_테스트상태
 [메서드명_테스트상태_기대결과](#메서드명_테스트상태_기대결과) 와 순서만 바뀐 Naming 방법으로 장단점은 동일하다.
  
```java
isAdult_False_AgeLessThan18(){}
withdrawMoney_ThrowsException_IfAccountIsInvalid(){}
admitStudent_FailToAdmit_IfMandatoryFieldsAreMissing(){}
```
  
## test\<테스트할 기능\> 
{: .notice}  
  테스트할 기능 앞에 test를 붙이는 Naming 방법으로 **코드의 악취를 방지**할 수 있지만, UnitTest가 문서화 됐을 경우에만 사용을 권장한다.
  
```java
testIsNotAnAdultIfAgeLessThan18(){}
testFailToWithdrawMoneyIfAccountIsInvalid(){}
testStudentIsNotAdmittedIfMandatoryFieldsAreMissing(){}
```
  
## <테스트할 기능> 
{: .notice}  
 [test <테스트할 기능 >](#test-테스트할-기능-) 과 장단점이 동일하다. 
{: .notice}  
  
```java
IsNotAnAdultIfAgeLessThan18(){}
FailToWithdrawMoneyIfAccountIsInvalid(){}
StudentIsNotAdmittedIfMandatoryFieldsAreMissing(){}
```
  
## should_기대결과_when_테스트상태
 테스트 목적을 쉽게 이해할 수 있지만 메서드 명이 길어진다는 단점이 있는 Naming 방법이다.
  
```java
should_ThrowException_When_AgeLessThan18(){}
should_FailToWithdrawMoney_ForInvalidAccount(){}
should_FailToAdmit_IfMandatoryFieldsAreMissing(){}
```
  
## when_테스트상태_Expect_기대결과
 [should_기대결과_when_테스트상태](#should_기대결과_when_테스트상태) 와 동일하게 테스트 목적을 쉽게 이해할 수 있지만 메서드명이 길어진다는 단점을 가지고 있다.
  
```java
When_AgeLessThan18_Expect_isAdultAsFalse(){}
When_InvalidAccount_Expect_WithdrawMoneyToFail(){}
When_MandatoryFieldsAreMissing_Expect_StudentAdmissionToFail(){}
```
  
## given_사전조건_When_테스트상태_기대결과
 함수명에 가장 많은 정보를 담은 Naming 방법이지만 함수명이 매우 길어질 수 있다는 단점이 있다.
  
```java
Given_UserIsAuthenticated_When_InvalidAccountNumberIsUsedToWithdrawMoney_Then_TransactionsWillFail
```

---
  
# 연결문서
