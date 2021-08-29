---

title: "블로그 댓글 기능 적용"
excerpt: "utterance 플랫폼을 활용한 댓글 기능 적용하기" 

categories:
  - GitHub
  - Blog

tags:
  - [jekyll, Minimal Mistake]

last_modified_at: 2021-08-29T08:06:00-05:00

---

- #### 목차
  - [utterance 소개](#utterance-소개)
  - [utterance 적용하기](#utterance-적용하기)
    - [Step1 : Comment용 git 저장소 생성](#step1--comment용-git-저장소-생성)
    - [Step2 : utterance 설치](#step2--utterance-설치)
    - [Step3 : 블로그에 반영할 script 코드 얻어오기](#step3--블로그에-반영할-script-코드-얻어오기)
    - [Step4 : 블로그에 적용하기](#step4--블로그에-적용하기)
  - [utterance 결과](#utterance-결과)
  - [에러 Fix](#에러-fix)

---

### utterance 소개  

　![image](/assets/images/Blog/UtteranceMain.png){: width="70%" height="70%"}  
 - 댓글 위젯을 제공하는 플랫폼
 - OpenSource
 - 광고가 없고 무료!
 - 여러가지 테마 지원
 - <span style="color:red">깃허브 계정을 사용하여 댓글 추가</span>

---

### utterance 적용하기

- #### Step1 : Comment용 git 저장소 생성
  - 댓글이 달리면 repository의 Issue 내역이 추가되고 그 내역을 이메일로 받아볼 수 있다
  - 블로그 repository가 Issue 내역으로 지저분해 지는 것이 싫다면 Comments용 Repository를 생성한다.  

　　　![image](/assets/images/Blog/UtteranceNewRepository.png){: width="70%" height="70%"}

- #### Step2 : utterance 설치
  - <https://github.com/apps/utterances> 링크로 이동하여 설치를 진행한다.


- #### Step3 : 블로그에 반영할 script 코드 얻어오기
  - <https://utteranc.es/> 링크로 이동한다.
  ![image](/assets/images/Blog/UtteranceGetScriptCode.png){: width="70%" height="70%"}
  - 붉은색 영역을 모두 작성하면 파란색 영역의 script 코드가 생성된다.

- #### Step4 : 블로그에 적용하기
  - Minimal Mistake를 사용하지 않는 경우에는 scipt 코드를 그대로 블로그 페이지에 복사하여 적용한다.
  - Minimal Mistake 사용자는 _config.yml 파일에 다음 부분을 수정한다.
 ![image](/assets/images/Blog/UtteranceConfigyml.png){: width="90%" height="90%"}
  - Minimal Mistake를 사용하는 경우에는 댓글 가로 영역이 좁게 보일 수 있다. -> _page.scss 파일에 아래와 같이 추가한다.  
 ![image](/assets/images/Blog/UtteranceSetWidth.png){: width="70%" height="70%"}
  - 변경사항을 Push 한다.

---

### utterance 결과
 - 댓글
 >![image](/assets/images/Blog/UtteranceResult.png){: width="70%" height="70%"}  

 - 깃허브 이슈
 >![image](/assets/images/Blog/UtteranceResultIssue.png){: width="70%" height="70%"}  

 - 이메일 알림
 >![image](/assets/images/Blog/UtteranceResultEmail.png){: width="70%" height="70%"}

---

### 에러 Fix
 - 댓글 작성시, 아래와 같은 에러 발생  
 ![image](/assets/images/Blog/UtteranceError.png){: width="70%" height="70%"}

- 조치
  - 깃허브 Repository에서 Application 설정 변경
  ![image](/assets/images/Blog/UtteranceErrorFix1.png){: width="70%" height="70%"}

  - Repository Access 설정에 Comments Repository를 추가해준다.
  ![image](/assets/images/Blog/UtteranceErrorFix2.png){: width="70%" height="70%"}
