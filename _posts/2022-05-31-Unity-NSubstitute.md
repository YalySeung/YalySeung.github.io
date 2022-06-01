---
title: "NSubstitute"
excerpt: "단위테스트 도우미"

categories:
  - Unity

tags:
  - [Unity, C#, UnitTest]

toc: true
toc_sticky: true
toc_label: "NSubstitute"

last_modified_at: 2022-05-31T08:00:00-10:00:00
---

# 개요
  - .Net에서 단위테스트 도구로 사용하는 DLL
  - Fake, Mock, Dummy, Spy 등을 사용 가능

# 환경구성
  1. NSubstitude Nuget 설치 => <https://www.nuget.org/downloads>
  ![image](/assets/images/Unity/UnitTest/NugetDownloadLink.png){: width="60%" height="60%"}
  2. 커맨드 창을 열어 다운받은 nuget.exe 파일 경로로 이동
  3. 커맨드라인 입력하여 실행
        nuget.exe Install NSubstitute.Analyzers.CSharp -Version 1.0.15
  ![image](/assets/images/Unity/UnitTest/NSubstituteInstall.png){: width="100%" height="100%"}
  4. DLL 파일을 저장하고자 하는 경로에 Import ! 이때, Castle.Core.dll 파일도 같은 경로에 import 해야함
  ![image](/assets/images/Unity/UnitTest/ImportNewAsset.png){: width="50%" height="50%"}

  ![image](/assets/images/Unity/UnitTest/NSubstituteImport.png){: width="50%" height="50%"}

  ![image](/assets/images/Unity/UnitTest/CastleCoreImport.png){: width="50%" height="50%"}
  5. Unity Play TestRunner 를 생성 한 후 Play Tests 파일에 Assembly References를 등록
  ![image](/assets/images/Unity/UnitTest/AssemblyReferenceInspector.png){: width="50%" height="50%"}

  Player TestRunner 생성 방법은 => [Unity TestRunner](https://yalyseung.github.io/unity/Unity-TestRunner/)

# 테스트 소스코드
