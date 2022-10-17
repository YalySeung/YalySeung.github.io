---
title: "Start Git Blog"
excerpt: "깃 블로그 시작하기"

categories:
- Blog

tags:
- [Blog]

toc: true
toc_sticky: true
toc_label: "Start Git Blog"

last_modified_at: 2022-10-17T08:00:00-10:00:00
---
# 개요
  - 서버 개발시, 무거운 Eclipse 대신 VSCode를 사용하여 개발하고자 하는 사람들을 위한 환경셋팅 방법을 소개하겠다.

# 필요한 Utility / Tool
- git

## Jekyll 테마 사용을 위해 필요
- Ruby
- Jekyll 과 Bundler

# 개발환경 구성
## git 설치
  [git 다운로드 링크](https://git-scm.com/downloads)
  - 셋업을 안내에따라 설치한다.
  - git 계정 생성과정은 생략하도록 하겠다.

## 블로그용 git repository 생성 및 clone
  - repository 생성
  - repository 이름은 <span style="color:red">username.github.io</span> 형식으로 생성해야한다!! => 깃헙 계정 기본설정은 계정당 1개의 블로그로 설정되어있다.  
  ![image](/assets/images/Blog/BlogRepository.png)  

  - Source Tree로 소스 Clone  
  ![image](/assets/images/Blog/GitRepositoryUrl.png)  
  위와 같이 url을 복사하여  
  ![image](/assets/images/Blog/CloneBlogRepository.png)  
  소스 Clone!

## Ruby 설치
  ![image](/assets/images/Blog/RubyDownload.png)  
  
  - Devkit 가 포함된 셋업을 설치해야한다.
  [Ruby 다운로드 링크](https://rubyinstaller.org/downloads/)  

  - 설치 과정에서 아래와같이 Add Ruby executables to your PATH 항목에 체크하여 환경변수가 자동으로 등록되도록 한다.  
  ![image](/assets/images/Blog/RubyInstall.png)  

## Jekyll과 Bundler 설치
  - 아래부터 환경 셋팅은 VSCode를 사용하도록 하겠다.(VSCode 설치 과정은 생략)
  [VSCode 다운로드 링크](https://code.visualstudio.com/download);  

  - Bundler는 루비 프로젝트 필요한 gem의 올바른 버전을 추적하고 설치하는 도구이다.
  - vscode 터미널에 다음 명령어들을 차례로 수행한다. (설치 및 버전 확인)
    - <span style="color:red">gem install jekyll bundler</span>
    - <span style="color:red">bundle update</span>  
    - <span style="color:red">jekyll -v</span>  
  ![image](/assets/images/Blog/VSCodeJekyllInstall.png)

## Jekyll 테마 적용
  - [테마 다운로드 링크](http://jekyllthemes.org/)
  - 가장 많이 사용되는 테마는 minimal mistakes를 적용해 보도록 하겠다. [minimal mistakes 다운로드 링크](https://github.com/mmistakes/minimal-mistakes)
  - 테마 zip 파일을 다운로드 받아서 위에서 지정했던 블로그 폴더 경로에 압축 해제한다.    
  ![image](/assets/images/Blog/MinimalMistakesDownloadResult.png)  
  - <span style="color:red">test 와 docs 폴더는 지워주도록 하자.</span>

## 로컬에서 블로그 확인하기
  - 터미널에 <span style="color:red">jekyll server</span> 명령어를 실행하면 블로그 내용을 확인 할 수 있다.  
  ![image](/assets/images/Blog/BlogInitResult.png)


## 에러 처리
  ![image](/assets/images/Blog/JekyllError.png)
  - 위와 같이 bundler의 파일을 찾지 못하는 경우 아래 명령어 실행
    - <span style="color:red">gem clean</span>
    - <span style="color:red">gem install bundler</span>
    - <span style="color:red">bundle install</span>
  
초기 설정 완료~!!

## 접근 url 설정
  - _config.yml : 블로그 설정파일  
  ![image](/assets/images/Blog/SetBlogUrl.png)  
  - url 값 변경하면 웹페이지에서 접근 가능

## git repository에 변경사항 push
  ![image](/assets/images/Blog/PostingCommit.png)  
  - 최초 반영되는데 시간이 좀 소요된다.

  ![image](/assets/images/Blog/GitHubBlogResult.png)  

[글 포스팅 하기로 이동~!](https://yalyseung.github.io/blog/Blog-PostContents/)
