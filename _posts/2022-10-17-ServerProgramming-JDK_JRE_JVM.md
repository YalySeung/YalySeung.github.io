---
title: "JDK, JRE, JVM"
excerpt: "JDK, JRE, JVM 이란 무엇인가"

categories:
- ServerProgramming

tags:
- [ServerProgramming]

toc: true
toc_sticky: true
toc_label: "JDK, JRE, JVM"

last_modified_at: 2022-10-24T08:00:00-10:00:00
---
# JRE
  - Java Runtime Environment
  - 소프트웨어를 실행하도록 설계된 소프트웨어의 일부
  - 클래스 라이브러리, 클래스로더, 자바명령, JVM등 으로 구성된 패키지

# JDK
  - Java Development Kit
  - Java 애플리케이션을 만드는 데 사용되는 소프트웨어 개발 환경
  - Java 프로그램을 만드는 도구 + 이를 실행하는 도구(JRE) => 모든 JDK 버전은 JRE와 함께 제공된다.
  - javac(컴파일러), jar(아카이브), jdb(디버거), Javadoc(문서 생성기) 등을 포함한다.  
  
  ![image](/assets/images/ServerProgramming/JDK_Bin.png){: width="70%" height="70%"}


# JVM
  - 자바 바이트 코드를 실행하는 Machine
  - 플랫폼에 의존적(Window, Linux.. 운영체제별 JVM 존재)
  - 컴파일된 바이트 코드는 어떤 JVM에서나 동작한다.
  - 바이트 코드 읽기, 검증, 실행, 실행환경의 규격 제공 등의 역할을 한다.

# 기타
## JAR
  - Java Archive
  - 압축 파일 포맷중 하나
  - 여러개의 자바 클래스 파일과 클래스들이 이용하는 관련 리소스 및 메타데이터를 하나의 파일로 모은 소프트웨어 패키지 파일 포맷