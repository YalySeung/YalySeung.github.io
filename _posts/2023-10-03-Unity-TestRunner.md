---
title : "TestRunner"
excerpt : "TestRunner"
toc : true
toc_sticky : true
toc_label : "TestRunner"
categories:
- Unity
tags:
- [Unity, UnitTest]
last_modified_at: 2023-10-03T08:00:00-10:00:00
---

# 날짜 : 2023-10-03 22:22

# 태그 :  #Unity #UnitTest
---

# 내용

## 개요
  - Unity Unit Test (단위테스트) 도구
  - PlayMode Test / EditMode Test

## 환경 설정

### Step1 : TestRunner 윈도우 Open  
  
![image](../../assets/Images/TestRunnerMenu.png){: width=350 height=350}  
![image](../../assets/Images/Arrow.png){: width=50 height=50}  
![image](../../assets/Images/TestRunnerWindow.png){: width=200 height=200}

### Step2 : Assembly Folder 생성
- 위 이미지의 Create EditMode Test Assembly Folder 버튼을 선택하여 테스트 폴더를 생성 => EditTest Assembly Definition 파일도 함께 생성됨  
  
![image](./../../assets/images/TestFolder%201.png)

### Step3 : 테스트 스크립트에서 사용할 Assembly 생성
- 스크립트 폴더 밑에 생성  
  ![image](CreateAssemblyDefinition.png)
  
![image](../../assets/Images/Arrow.png){: width=50 height=50}   
![image](../../assets/Images/ScriptAssemblyDefinition.png) 

### Step4 : EditTests Assembly Definition 파일에 Script Assembly Definition 파일 연결
    
![image](../../assets/Images/AssemblyDefinitionInspector.png)

---  

## 테스트 스크립트 작성

### 스크립트 생성
  
![image](../../assets/Images/TestRunnerScriptMenu.png)

### TestScript Attribute
- [Setup] : EditMode 테스트 테스트 메서드 전, 테스트 환경 구성
- [Test] : EditMode 테스트
- [UnitySetup] : PlayMode 테스트 테스트 메서드 전, 테스트 환경 구성
- [UnityTest] : PlayMode 테스트

### PlayMode 테스트 스크립트 샘플

```c#
  public class TestMoveOnePointToXPos
  {
	  GameObject testObject;

	  [UnitySetUp]
	  public IEnumerator Setup()
	  {
		  testObject = new GameObject("testGameObject");
		  yield return null;
	  }

	  [UnityTest]
	  public IEnumerator TestMoveOnePointToXPos_MoveOneToX()
	  {
		  Vector3 expectedPos = new Vector3(1, 0, 0);
		  testObject.transform.position = Vector3.zero;

		  testObject.AddComponent<MoveOnePointToXPos>();

		  yield return null;

		  Assert.AreEqual(expectedPos, testObject.transform.position);

	  }
  }  
```

![image](../../assets/Images/TestRunnerWindowRun.png)
테스트를 실행하면 검증에 성공!

---

# 연결문서

