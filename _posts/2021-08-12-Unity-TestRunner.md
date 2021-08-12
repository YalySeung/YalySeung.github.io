---
title: "UnitTest"
excerpt: "TestRunner" 

categories:
  - Unity

tags:
  - [Unity]

last_modified_at: 2021-08-12-T08:06:00-05:00
---


### 개요
 - Unity Unit Test (단위테스트) 도구
 - PlayMode Test / EditMode Test

---

### 환경 설정
 - #### Step1 : TestRunner 윈도우 Open  
![image](/assets/images/Unity/UnitTest/TestRunnerMenu.png){: width="60%" height="60%"}  
   
     ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/Unity/UnitTest/TestRunnerWindow.png){: width="30%" height="30%"}

 - #### Step2 : Assembly Folder 생성
   - 위 이미지의 Create EditMode Test Assembly Folder 버튼을 선택하여 테스트 폴더를 생성 => EditTest Assembly Definition 파일도 함께 생성됨  
   ![image](/assets/images/Unity/UnitTest/TestFolder.png){: width="30%" height="30%"} 

 - #### Step3 : 테스트 스크립트에서 사용할 Assembly 생성
   - 스크립트 폴더 밑에 생성  
 ![image](/assets/images/Unity/UnitTest/CreateAssemblyDefinition.png){: width="70%" height="70%"}  
   
      ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/Unity/UnitTest/ScriptAssemblyDefinition.png){: width="40%" height="40%"}

 - #### Step4 : EditTests Assembly Definition 파일에 Script Assembly Definition 파일 연결
 ![image](/assets/images/Unity/UnitTest/AssemblyDefinitionInspector.png){: width="50%" height="50%"}  


 ---  

### 테스트 스크립트 작성

 - #### 스크립트 생성
![image](/assets/images/Unity/UnitTest/TestRunnerScriptMenu.png){: width="70%" height="70%"}  

 - #### TestScript Attribute
   - [Setup] : EditMode 테스트 테스트 메서드 전, 테스트 환경 구성
   - [Test] : EditMode 테스트
   - [UnitySetup] : PlayMode 테스트 테스트 메서드 전, 테스트 환경 구성
   - [UnityTest] : PlayMode 테스트
 
 - #### PlayMode 테스트 스크립트 샘플
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

   ![image](/assets/images/Common/Arrow.png){: width="10%" height="10%"} ![image](/assets/images/Unity/UnitTest/TestRunnerWindowRun.png){: width="40%" height="40%"} 

　　테스트를 실행하면 검증에 성공!