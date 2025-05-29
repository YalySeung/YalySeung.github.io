---
title : "JNI"
excerpt : "JNI"
toc : true
toc_sticky : true
toc_label : "JNI"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-03-19T08:00:00-10:00:00
---
  
---
  
## 📌 JNI(Java Native Interface)란?

> **info**
>
> JNI는 Java 애플리케이션이 **네이티브 코드(C, C++ 등)**를 호출하거나, 네이티브 코드에서 Java 메서드를 호출할 수 있도록 해주는 **Java 표준 인터페이스**이다.  
> 플랫폼 의존적인 기능, 시스템 API 호출, 성능 최적화 목적 등으로 사용된다. 
{: .notice--info}  

---
  
## ✅ JNI 사용 목적

- **성능 최적화**: 고성능 처리를 C/C++로 구현하고 Java에서 호출
- **시스템/하드웨어 접근**: Java에서 접근할 수 없는 로우레벨 기능 구현
- **기존 네이티브 라이브러리 재활용**: C/C++로 작성된 모듈을 Java에서 호출
- **양방향 호출 지원**: Java → C, C → Java 양방향 지원

---
  
## ✅ 주요 사용 예
  
### 🔹 Java → Native 호출
  
```java
public class MyNativeApp {
    static {
        System.loadLibrary("mylib"); // libmylib.so or mylib.dll 로딩
    }

    public native int nativeAdd(int a, int b);

    public static void main(String[] args) {
        MyNativeApp app = new MyNativeApp();
        int result = app.nativeAdd(2, 3);
        System.out.println(result);
    }
}
```
  
```c
// mylib.c
  
#include <jni.h>
  
#include "MyNativeApp.h"

JNIEXPORT jint JNICALL Java_MyNativeApp_nativeAdd(JNIEnv *env, jobject obj, jint a, jint b) {
    return a + b;
}
```

---
  
### 🔹 Native → Java 호출
  
```c
// 예시: JVM 환경에서 Java 클래스 메서드 호출
JNIEnv* env;
jclass cls = (*env)->FindClass(env, "com/example/MyClass");
jmethodID mid = (*env)->GetMethodID(env, cls, "printMessage", "()V");
(*env)->CallVoidMethod(env, obj, mid);
```

---
  
## ✅ JNI 빌드 및 실행 순서

1. Java 클래스에 `native` 선언
2. `javac`, `javah` 또는 `javac -h`로 헤더 파일 생성
3. C/C++로 구현 파일 작성 및 컴파일 → `.so`, `.dll`
4. Java에서 `System.loadLibrary()`로 네이티브 라이브러리 로드
5. 실행

---
  
## ✅ JNI 사용 시 주의사항

- **플랫폼 종속적**: OS마다 컴파일 방식, 파일 확장자 상이
- **메모리 누수 주의**: C/C++의 수동 메모리 관리 필요
- **디버깅 복잡성**: JVM ↔ Native 간 오류 추적이 복잡
- **성능 최적화는 선택적**: 대부분의 애플리케이션은 순수 Java로 충분

---
  
# 연결문서
- [JVM](../../java/java-JVM)
