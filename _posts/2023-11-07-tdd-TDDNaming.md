---
title : "TDDNaming"
excerpt : "TDDNaming"
toc : true
toc_sticky : true
toc_label : "TDDNaming"
categories:
- TDD
tags:
- [Test, TDD, CleanCode]
last_modified_at: 2023-11-07T08:00:00-10:00:00
---

# 날짜 : 2023-11-07 14:02

# 태그 : #Test #TDD #CleanCode 
---

# 내용

## TDD 함수 Naming 전략

### 메서드명_테스트상태_기대결과
- 코드 리팩토링으로 인한 메서드명 변경시, 테스트도 변경되어야한다.

#### Example
- isAdult_AgeLessThan18_False
- withdrawMoney_InvalidAccount_ExceptionThrown
- admitStudent_MissingMandatoryFields_FailToAdmit

### 메서드명_기대결과_테스트상태
- [메서드명_테스트상태_기대결과](#메서드명_테스트상태_기대결과) 와 순서만 빠뀐 naming rule

#### Example
- isAdult_False_AgeLessThan18
- withdrawMoney_ThrowsException_IfAccountIsInvalid
- admitStudent_FailToAdmit_IfMandatoryFieldsAreMissing

### test\<테스트할 기능\>
- 코드 악취 방지
- 문서화된 UnitTest에 권장

#### Example
- testIsNotAnAdultIfAgeLessThan18
- testFailToWithdrawMoneyIfAccountIsInvalid
- testStudentIsNotAdmittedIfMandatoryFieldsAreMissing

### <테스트할 기능>
- [테스트할 기능](#test-테스트할-기능-) 과 동일

#### Example
- IsNotAnAdultIfAgeLessThan18
- FailToWithdrawMoneyIfAccountIsInvalid
- StudentIsNotAdmittedIfMandatoryFieldsAreMissing

### should_기대결과_when_테스트상태
- 쉽게 이해할 수 있기 때문에 많이 사용되는 naming rule

#### Example
1. - - should_ThrowException_When_AgeLessThan18
        - should_FailToWithdrawMoney_ForInvalidAccount
        - should_FailToAdmit_IfMandatoryFieldsAreMissing

### when_테스트상태_Expect_기대결과

#### Example
- When_AgeLessThan18_Expect_isAdultAsFalse
- When_InvalidAccount_Expect_WithdrawMoneyToFail
- When_MandatoryFieldsAreMissing_Expect_StudentAdmissionToFail

### given_사전조건_When_테스트상태_기대결과
- [BDD](../../bdd/bdd-BDD)에서 사용하는 naming rule

#### Example
- Given_UserIsAuthenticated_When_InvalidAccountNumberIsUsedToWithdrawMoney_Then_TransactionsWillFail

---

# 연결문서
