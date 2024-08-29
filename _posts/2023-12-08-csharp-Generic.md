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
  
---
  
## 정의
> **C#에서 Generic은?**  
>
> Class 나 Method에서 사용할 내부 데이터 타입을 컴파일 시점에 미리 지정하는 Syntax를 의미한다. 
{: .notice--info}  
  
## Generic을 사용하는 이유
 Generic을 사용함으로써, 얻을 수 있는 장점은 무엇이 있을까?
 동일한 구조의 함수에 반환 형식이나 입력 형식만  다를 경우 여러 메서드를 오버로딩 해야하는데, Generic을 사용하면 **하나의 함수로 대체가 가능**하다. 따라서 **가독성**과 **형식 안정성**이 증가한다. 또한 생성 시점에 타입을 명시하기 때문에 **타입 검사가 불필요**하며, **InvalidCastingException 예외를 회피**할 수 있다. 또한 [boxing](../../csharp/csharp-boxing-unboxing#boxing은-무엇일까)을 피하여 메모리를 절약할 수 있다.
  
## Generic의 사용법
 class 선언에 **형식 매개변수인 \<T\>를 사용하여 선언**한다. 그리고 **생성자에서 모든 필드 값을 초기화** 해준다.
  
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

 Generic 클래스를 사용할 때는 **new 키워드 사용 시점**에 **Type을 명시**하여 객체를 생성한다.
  
```c#
main(){
  Generic<int> generic = new Generic<int>();
  Console.WriteLine(generic.One);
  ...
}
```

---
  
# 연결문서
- [boxing unboxing](../../csharp/csharp-boxing-unboxing)