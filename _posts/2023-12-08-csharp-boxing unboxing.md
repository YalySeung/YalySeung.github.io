---
title : "boxing unboxing"
excerpt : "boxing unboxing"
toc : true
toc_sticky : true
toc_label : "boxing unboxing"
categories:
- CSharp
tags:
- [프로그래밍언어, CSharp]
last_modified_at: 2023-12-08T08:00:00-10:00:00
---

# 날짜 : 2023-12-08 11:32

# 태그 : #프로그래밍언어 #CSharp
---

# 내용

## 정의
> **boxing 과 unboxing이란?**
>
> C# 개발의 사용 편의성을 위한 기능 
{: .notice--info}

## boxing
- boxing은 값 형식을 형식 또는 이 값 형식에서 구현된 임의의 인터페이스 형식으로 변환하는 프로세스
- CLR은 값 형식을 boxing할 때 값을 System.Object 인스턴스 내부에 래핑하고 관리되는 힙에 저장
- unboxing하면 개체에서 값 형식이 추출

```c#
int i = 123;
object o = i; //암시적 boxing
```

- boxing 된 123 값은 heap 영역에 저장됨

## unboxing
- unboxing은 object 형식에서 object로 또는 인터페이스 형식에서 해당 인터페이스를 구현하는 값 형식으로 명시적 변환하는 프로세스
- unboxing 과정
- 개체 인스턴스가 지정한 값 형식을 boxing 한 값인지 확인
- 인스턴스의 값을 값 형식 변수에 copy
- 부적절한 형식으로 unboxing 할 경우 InvalidCastingException 발생

```c#
int i = 123;
object o = i;
int j = (int)o; //unboxing
```

---

# 연결문서
