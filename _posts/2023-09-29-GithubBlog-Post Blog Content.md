---
title : "Post Blog Content"
excerpt : "Post Blog Content"
toc : true
toc_sticky : true
toc_label : "Post Blog Content"
categories:
- GithubBlog
tags:
- [Github, Blog]
last_modified_at: 2023-09-29T08:00:00-10:00:00
---

# 날짜 : 2023-09-29 09:17

# 태그 : #Github #Blog 
---

# 내용

## 개요
- 글을 포스팅 하는 방법을 알아보자
- 사용할 툴은 이전 글과 동일하게 VSCode로 진행하겠다.

## 새 글 게시

### _posts 폴더 및 게시글 생성
  ![image](./../../assets/images/../../assets/Images/MakePostFolderAndMdFile.png)
-  md 파일 포멧 : yyyy-MM-dd-카테고리명-타이틀명.md

### 게시글 내용 작성 .md파일
  ```
  ---
  title:  "샘플 포스팅"
  excerpt: "새 글을 포스팅 해보자"

  categories:
    - Blog
  tags:
    - [Blog]

  toc: true
  toc_sticky: true
  
  date: 2022-10-17
  last_modified_at: 2022-10-17
  ---

  ## 블로그 내용 블라블라 마크다운 문법으로 작성

  ### 이상여기까지입니다.

  ```

#### 항목별 설명
  - title : 글 제목
  - excerpt : 글 내용 요약
  - categories, tags : 글 분류시 사용
  - toc : (Table of Contents) 포스트의 헤더들만 보여주는 목차 사용 여부
  - toc_sticky : 스크롤 시, 목차도 같이 이동시킬지 여부
  - date, last_modified_at : 글 작성과 수정일 표기

### 추가한 파일 git repository에 push 하면 끝!

---

# 연결문서
- [MarkDown Syntax](../../Markdown/Markdown-MarkDown-Syntax) 

