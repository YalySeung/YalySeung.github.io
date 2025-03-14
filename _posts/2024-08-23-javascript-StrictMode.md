---
title : "StrictMode"
excerpt : "StrictMode"
toc : true
toc_sticky : true
toc_label : "StrictMode"
categories:
- javascript
tags:
- [React, Study]
last_modified_at: 2024-08-23T08:00:00-10:00:00
---
  
---
  
> **Strict mode 란?**  
>
> JavaScript에서 코드를 더 엄격한 규칙으로 실행하도록 하는 기능이다. 
{: .notice--info}  
  
## Strict Mode 개요
 JavaScript의 Strict mode는 ES5에서 도입된 기능으로, 더 엄격한 코드 실행을 강제하여 **잠재적인 오류를 방지**하고 **안정성을 향상**시킨다.
  
## Strict Mode 적용 방법
 엄격 모드는 `use strict` 지시어를 사용하여 적용할 수 있다.
  
```javascript
"use strict";
```

 전역적으로 선언하면 스크립트 전체에 적용되며, 함수 내부에 선언하면 해당 함수에만 적용된다.
  
```javascript
function strictFunction() {
    "use strict";
    // 해당 함수 내부에서만 Strict Mode 적용
}
```
  
## Strict Mode 주요 특징
  
### 1️⃣ 암묵적 전역 변수 방지
 Strict mode에서는 변수를 선언하지 않고 사용할 경우 오류가 발생한다.
  
```javascript
// 비엄격 모드
x = 10; // 전역 변수를 암묵적으로 선언 가능

// 엄격 모드
"use strict";
y = 10; // 에러 발생: y is not defined
```
  
### 2️⃣ `this`의 기본 값 변경
 Strict mode에서는 `this`가 `undefined`로 설정된다.
  
```javascript
function myFunction() {
    console.log(this);
}

// 비엄격 모드
myFunction(); // 전역 객체 (window) 출력

// 엄격 모드
"use strict";
myFunction(); // undefined 출력
```
  
### 3️⃣ 중복된 매개변수 사용 금지
 Strict mode에서는 함수의 매개변수 이름이 중복될 경우 오류가 발생한다.
  
```javascript
"use strict";
function sum(a, a, c) { // 에러 발생: Duplicate parameter name not allowed
    return a + b + c;
}
```
  
### 4️⃣ 읽기 전용 속성 삭제 불가
 `Object.defineProperty()`로 `configurable: false` 속성을 설정한 경우, 해당 속성을 삭제할 수 없다.
  
```javascript
"use strict";
var obj = {};
Object.defineProperty(obj, "x", { value: 10, configurable: false });
delete obj.x; // 에러 발생: Cannot delete property 'x' of #<Object>
```
  
### 5️⃣ 예약어 사용 제한
 JavaScript에서 예약된 키워드를 변수명이나 함수명으로 사용할 수 없다.
  
```javascript
"use strict";
var let = 10; // 에러 발생: Unexpected strict mode reserved word
```

---
  
# 연결문서
