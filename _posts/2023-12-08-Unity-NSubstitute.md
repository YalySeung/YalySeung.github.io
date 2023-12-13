---
title : "NSubstitute"
excerpt : "NSubstitute"
toc : true
toc_sticky : true
toc_label : "NSubstitute"
categories:
- Unity
tags:
- [Unity]
last_modified_at: 2023-12-08T08:00:00-10:00:00
---

# 날짜 : 2023-12-08 11:44

# 태그 : #Unity 
---

# 내용

## 정의
> NSubstitute란?
> .NET 에서 단위테스트 도구로 사용되는 DLL

## 환경구성

### NSubstitude Nuget 설치
- <https://www.nuget.org/downloads>
  
![image](../../assets/images/NugetDownloadLink.png){: width="60%" height="60%"}

### 커맨드 창을 열어 다운받은 nuget.exe 파일 경로로 이동

### 커맨드라인 입력하여 실행

```bash
nuget.exe Install NSubstitute.Analyzers.CSharp -Version 1.0.15
```
  
![image](../../assets/images/NSubstituteInstall.png){: width="100%" height="100%"}

### DLL 파일을 저장하고자 하는 경로에 Import 
- 이때, Castle.Core.dll 파일도 같은 경로에 import 해야함
  
![image](../../assets/images/ImportNewAsset.png){: width="50%" height="50%"}

![image](../../assets/images/NSubstituteImport.png){: width="50%" height="50%"}

![image](../../assets/images/CastleCoreImport.png)  {: width="50%" height="50%"}

### Unity Play TestRunner 를 생성 한 후 Play Tests 파일에 Assembly References를 등록
  
![image](../../assets/images/AssemblyReferenceInspector%201.png){: width="50%" height="50%"}

Player TestRunner 생성 방법은 => [TestRunner](../../unity/Unity-TestRunner) 참고  

## 테스트

### 소스코드
- 간단한 테스트를 통해 몇가지 함수를 확인

```c#
//Mock 생성을 위한 인터페이스 정의
public interface ITestObj
{
	public int PropertyValue { get; set; }
	public void DoNothing(int input);
	public int AddOne(int input);
}

// 단위테스트
public class TestTestObj
{
	ITestObj testObj;

	[SetUp]
	public void SetUp()
	{
		testObj = Substitute.For<ITestObj>(); // Mock Instance 생성
		testObj.AddOne(1).Returns(2); // 반환값이 있는 함수의 리턴값 정의
		testObj.PropertyValue.Returns(2); // Property 반환값 정의
	}

	[UnityTest]
	public IEnumerator TestTestObjAddOne()
	{
		Debug.Log($"AddOne(1) : {testObj.AddOne(1)}");
		Assert.AreEqual(2, testObj.AddOne(1));
		testObj.DoNothing(3);

		// 반환값이 없는 함수가 호출되었는지에 대한 검증
		testObj.Received().DoNothing(3);

		// 반환값이 없는 함수가 호출되지 않았는지에 대한 검증
		//testObj.DidNotReceive().AddOne(2);

		yield return null;
	}
}
```

### 결과
  
![image](../../assets/images/NSubstituteUnitTestResult.png){: width="70%" height="70%"}

---

# 연결문서
- [TestRunner](../../unity/Unity-TestRunner)