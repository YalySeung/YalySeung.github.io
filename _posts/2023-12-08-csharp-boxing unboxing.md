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
  
---
  
> **boxing 과 unboxing이란?**  
>
> C# 개발의 사용 편의성을 위한 기능 중 하나로 Type에 대한 자동 변환을 지원한다. 
{: .notice--info}  
  
## boxing은 무엇일까
 boxing은 **값 형식**을 **참조형식**으로 변환하는 프로세스를 말한다. CLR은 값 형식을 boxing할 때, **System.Object 인스턴스 내부에 래핑하고 관리되는 힙에 저장**한다. 아래 예시는 **int type 변수**가 **object 타입**으로 **boxing** 되는 것을 보여준다. 여기서 boxing 된 123 이라는 값은 **heap 영역에 저장**된다.
  
```c#
int i = 123;
object o = i; //암시적 boxing
```
  
## unboxing은 무엇일까
 unboxing은 **boxing 했던 값을 다시 원상복귀** 시키는 프로세스를 말한다. unboxing 과정은 개체 인스턴스가 지정한 값 형식을 **boxing 한 값인지 확인**하고, 인스턴스의 **값을 값 형식 변수에 copy**한다. 이 과정에서 부적절한 형식으로 unboxing 할 경우 **InvalidCastingException** 발생한다. 아래는 boxing된 123 값을 unboxing 하는 예시이다.
  
```c#
int i = 123;
object o = i;
int j = (int)o; //unboxing
```

---
  
# 연결문서
