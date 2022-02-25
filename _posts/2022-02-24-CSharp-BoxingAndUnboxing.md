---
title: "Boxing / Unboxing"
excerpt: "Auto Casting"

categories:
  - CSharp

tags:
  - [CSharp]

toc: true
toc_sticky: true
toc_label: "Boxing / Unboxing"

last_modified_at: 2022-02-24T08:00:00-10:00:00
---

# 개요
  - C# 개발의 사용 편의성을 위한 기능
  - boxing과 unboxing을 수행하는 데 많은 계산 과정이 필요(비용 증가)

# boxing
  - boxing은 값 형식을 형식 또는 이 값 형식에서 구현된 임의의 인터페이스 형식으로 변환하는 프로세스
  -  CLR은 값 형식을 boxing할 때 값을 System.Object 인스턴스 내부에 래핑하고 관리되는 힙에 저장
  - unboxing하면 개체에서 값 형식이 추출
  - ex)
    ```c#
      int i = 123;
      object o = i; //암시적 boxing
    ```
  - boxing 된 123 값은 heap 영역에 저장됨

# unboxing
  - unboxing은 object 형식에서 object로 또는 인터페이스 형식에서 해당 인터페이스를 구현하는 값 형식으로 명시적 변환하는 프로세스
  - unboxing 과정
    - 개체 인스턴스가 지정한 값 형식을 boxing 한 값인지 확인
    - 인스턴스의 값을 값 형식 변수에 copy
  - 부적절한 형식으로 unboxing 할 경우 InvalidCastingException 발생
  - ex)
    ```c#
      int i = 123;
      object o = i;
      int j = (int)o; //unboxing
    ```
