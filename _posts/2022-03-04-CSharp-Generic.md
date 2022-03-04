---
title: "Generic"
excerpt: "형식 지원 패러다임"

categories:
  - CSharp

tags:
  - [CSharp]

toc: true
toc_sticky: true
toc_label: "Generic"

last_modified_at: 2022-03-04T08:00:00-10:00:00
---

# 개요
  - 클래스를 디자인 할때가 아니라 클래스를 사용할 때 타입을 지정함
  - 패턴 구현 코드를 재사용 가능
  - 오버로딩 줄일 수 있음

# 장점
  - 형식 안정성 증가
  - InvalidCastingException 예외 발생 X
  - Boxing을 피하여 메모리를 절약
  - 가독성증가
  - 타입 검사 불필요

# 활용
  - 이름에 접두어로 \<T> 사용 -> 형식 매개변수
  - 생성자에서 모든 필드값 초기화
  - ex) 선언
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
  - ex) 사용
    ```c#
    main(){
      Generic<int> generic = new Generic<int>();
      Console.WriteLine(generic.One);
      ...
    }
    ```
