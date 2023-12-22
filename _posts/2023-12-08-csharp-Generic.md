---
title : "Generic"
excerpt : "Generic"
toc : true
toc_sticky : true
toc_label : "Generic"
categories:
- CSharp
tags:
- [프로그래밍언어, CSharp]
last_modified_at: 2023-12-08T08:00:00-10:00:00
---

# 날짜 : 2023-12-08 11:39

# 태그 : #프로그래밍언어 #CSharp
---

# 내용

## 정의
> C#에서 Generic은?
> 클래스를 디자인 할때가 아니라 클래스를 사용할 때 타입을 지정함

## 장점
- 패턴 구현 코드를 재사용 가능
- 오버로딩 줄일 수 있음
- 형식 안정성 증가
- InvalidCastingException 예외 발생 X
- Boxing을 피하여 메모리를 절약
- 가독성증가
- 타입 검사 불필요

## 활용
- 이름에 접두어로 \<T> 사용 -> 형식 매개변수
- 생성자에서 모든 필드값 초기화

### 선언

```c#
class Generic<T>
{
  public Generic()
  {
	this.One = default(T);
	this.Two = default(T);
  }
  ...
}
```

### 사용

```c#
main(){
  Generic<int> generic = new Generic<int>();
  Console.WriteLine(generic.One);
  ...
}
```

---

# 연결문서
