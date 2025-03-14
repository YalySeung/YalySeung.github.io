---
title : "Type vs Interface"
excerpt : "Type vs Interface"
toc : true
toc_sticky : true
toc_label : "Type vs Interface"
categories:
- TypeScript
tags:
- [프로그래밍언어, TypeScript]
last_modified_at: 2024-05-03T08:00:00-10:00:00
---
  
---
  
> **Type vs Interface 차이점**  
>
>  TypeScript에서 객체의 타입을 정의할 때 `type`과 `interface` 모두 사용할 수 있다. 
{: .notice--info}  

  하지만 둘 사이에는 몇 가지 차이점이 존재하며, **상황에 따라 적절한 선택을 해야 한다.**  
  
## 📌 Type과 Interface의 주요 차이점
  
| 비교 항목        | `type` | `interface` |
| -------------- | ------ | ---------- |
| 확장(extends)  | `&` (intersection) | `extends` 키워드 |
| 중복 선언 가능 여부 | ❌ 불가능 | ✅ 가능 (자동 병합) |
| Mapped Type 사용 | ✅ 가능 | ❌ 불가능 |
| 인덱스 시그니처 지원 | ✅ 가능 | ✅ 가능 |
| 클래스에서 사용 | ✅ 가능 | ✅ 가능 |
  
## 📌 Type 사용 예제
  
```typescript
type User = {
    name: string;
    age: number;
};

type Admin = User & {
    isAdmin: boolean;
};

const adminUser: Admin = {
    name: "홍길동",
    age: 30,
    isAdmin: true,
};
```
  
## 📌 Interface 사용 예제
  
```typescript
interface User {
    name: string;
    age: number;
}

interface Admin extends User {
    isAdmin: boolean;
}

const adminUser: Admin = {
    name: "홍길동",
    age: 30,
    isAdmin: true,
};
```
  
## 📌 Type과 Interface 선택 기준
  
### ✅ `type`을 선택해야 하는 경우
- **Mapped Type**을 사용할 때  
- **유니온(`|`) 및 인터섹션(`&`) 타입을 활용할 때**  
- **단순한 객체 구조를 정의할 때**  
  
### ✅ `interface`를 선택해야 하는 경우
- **클래스와 함께 사용할 때**  
- **객체 타입을 확장할 가능성이 높을 때**  
- **자동 병합 기능을 활용해야 할 때**  
  
## 📌 결론
- **확장 가능성을 고려할 경우 `interface`가 더 적합**  
- **유연한 타입 조합이 필요할 경우 `type`이 유리**  
- **프로젝트 스타일에 따라 일관된 방식 선택이 중요**  

---
  
# 연결문서
