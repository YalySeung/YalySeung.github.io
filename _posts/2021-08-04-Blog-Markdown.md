---
title: "Markdown Syntax"
excerpt: "Markdown 작성요령" 

categories:
  - GitHub
  - Blog

tags:
  - [jekyll, Minimal Mistake]

last_modified_at: 2021-09-06T08:06:00-05:00
---

### 목차
  - [마크다운 문법 표기](#마크다운-문법-표기)
  - [중첩 구조 표현](#중첩-구조-표현)
  - [헤더](#헤더)
  - [텍스트 강조](#텍스트-강조)
  - [텍스트 기울임](#텍스트-기울임)
  - [텍스트 굵고 기울임](#텍스트-굵고-기울임)
  - [텍스트 가로줄](#텍스트-가로줄)
  - [텍스트 밑줄](#텍스트-밑줄)
  - [텍스트 글자색](#텍스트-글자색)
  - [텍스트 개행](#텍스트-개행)
  - [텍스트 공백, 들여쓰기](#텍스트-공백-들여쓰기)
  - [Inline 코드블럭](#inline-코드블럭)
  - [링크](#링크)
  - [텍스트 링크](#텍스트-링크)
  - [텍스트 개행](#텍스트-개행)
  - [파일 내에서 문단이동](#파일-내에서-문단이동)
  - [그림 삽입](#그림-삽입)
  - [그림 링크 삽입](#그림-링크-삽입)
  - [텍스트 개행](#파일-내에서-문단이동)
  - [인용문](#인용문)
  - [주석](#주석)
  - [순서 없는 리스트](#순서-없는-리스트)
  - [순서 있는 리스트](#순서-있는-리스트)
  - [체크리스트](#체크리스트)
  - [구분선](#구분선)
  - [테이블](#테이블)
  - [주석](#주석)
  - [접기 펼치기](#접기-펼치기)
  - [버튼](#버튼)

---

# 마크다운 문법 표기
## 마크다운 Syntax 앞에 "\\"를 붙인다.
### **markdown ex)**  
\\\<br/>
### **result)**  
\<br/>

---

# 중첩 구조 표현
  - \- 내용
  - **markdown ex)**  
  \- 대분류  
  \- 중분류  
  \- 소분류  
  - **result)**
    - 대분류
      - 중분류
         - 소분류

# 헤더
  - \# 사용
  - **markdown ex)**  
  \# h1  
  \## h2  
  \### h3  
  \#### h4  
  \##### h5  
  \###### h6  
  - **result)**  
# h1
## h2
### h3
#### h4
##### h5
###### h6

---
# 텍스트 강조
  - **markdown ex)**  
  \*\*텍스트\*\*
  - **result)**  
  **텍스트**

# 텍스트 기울임
- **markdown ex)**  
\*텍스트\*
- **result)**  
*텍스트*

# 텍스트 굵고 기울임
- **markdown ex)**  
\*\*\*텍스트\*\*\*
- **result)**  
***텍스트***

# 텍스트 강조
- **markdown ex)**  
\*\*텍스트\*\*
- **result)**  
**텍스트**

# 텍스트 가로줄

- **markdown ex)**  
\~\~텍스트\~\~
- **result)**  
~~텍스트~~

# 텍스트 밑줄
- **markdown ex)**  
\<u>텍스트\</u>
- **result)**  
<u>텍스트</u>

# 텍스트 글자색
- **markdown ex)**  
\<span style="color:red">텍스트\</span>
- **result)**  
<span style="color:red">텍스트</span>

# 텍스트 개행
- **markdown ex)**  
첫줄[공백][공백][개행문자]
둘째줄
- **result)**  
첫줄  
둘째줄

# 텍스트 공백, 들여쓰기
- **markdown ex)**  
전각 문자 사용! ==> (　)
- **result)**  
　　들여쓰기


---

# Inline 코드블럭
  - \```언어이름
  코드
  \```
  - **markdown ex)**  
  \```c#
  using system;  
  class Sample{  
    public Sample(){  
  
    }  
  }
  \```
  - **result)**  
  ```c#
  using system;
      class Sample{
        public Sample(){

        }
      }
  ```
    스페이스바 4번으로도 가능


---

# 링크
- **markdown ex)**  
\<https://www.google.com>
- **result)**  
<https://www.google.com>

# 텍스트 링크
- **markdown ex)**  
[구글페이지]\(https://www.google.com)
- **result)**  
[구글페이지](https://www.google.com)


# 파일내에서 문단 이동
  - 방법 
  1. 헤더 제목 문자열 복사 후 (문단의 주소)에 복사
  2. 특수문자 제거
  3. 공백을 -로 변경
  4. 대문자를 소문자로 변경

  - **markdown ex)**  
  [Inline 코드블럭]\(#inline-코드블럭)
  - **result)**  
  [Inline 코드블럭](#inline-코드블럭)

---
# 그림 삽입
  - **markdown ex)**  
  ![image]\(이미지주소){: width="20%" height="20%"}
  - **result)**  
  ![image](/assets/images/Blog/LinkImage.jpg){: width="20%" height="20%"}

# 그림 링크 삽입
  - **markdown ex)**  
  \[![image]\(이미지 경로)](링크주소)
  - **result)**  
  [![image](/assets/images/Blog/LinkImage.jpg)](#inline-코드블럭)

  ---
# 인용문
  - **markdown ex)**  
  \>인용문
    \>>중첩 인용문
  - **result)**  
  > 인용문
    >> 중첩인용문

# 주석
  - **markdown ex)**  
  \<cite>google\</cite> --- google-forum' Conference, 1997
  - **result)**  
  <cite>google</cite> --- google-forum' Conference, 1997

  ---
# 순서 없는 리스트
  - **markdown ex)**  
  \- depth1  
    \* depth2  
      \+ depth3  
    \* depth2  
  \- depth1  
  - **result)**  
  - depth1
    * depth2
      + depth3
    * depth2
  - depth1

# 순서 있는 리스트
- **markdown ex)**  
1. depth1_1
2. dqpth1_2
   1. depth2_1  
      \- depth3_1  
      \- depth3_2
   1. depth2_2  
      \- depth3_3  
      \- depth3_4
- **result)**  
1. depth1_1
2. dqpth1_2  
   1. depth2_1  
      - depth3_1  
      - depth3_2
   1. depth2_2  
      - depth3_3  
      - depth3_4


# 체크리스트
  - **markdown ex)**  
  \- [ ] 체크 안됨
  \- [x] 체크 됨
  - **result)**  
  - [ ] 체크 안됨
  - [x] 체크 됨

# 구분선
  - **markdown ex)**  
  \---
  \***
  - **result)**  
  ---
  ***

---
# 테이블
  - **markdown ex)**  
  |제목|내용|설명|
  |:---|---: |:---: |
  |좌측정렬|우측정렬|가운데정렬|
  |좌측정렬|**우측정렬 진하게**|가운데정렬|
  |좌측정렬|<span style="color:red">우측정렬Red</span>|가운데정렬|

  - **result)**  

  |제목|내용|설명|
  |:---|---:|:---:|
  |좌측정렬|우측정렬|가운데정렬|
  |좌측정렬|**우측정렬 진하게**|가운데정렬|
  |좌측정렬|<span style="color:red">우측정렬Red</span>|가운데정렬|


---

# 접기 펼치기
  - **markdown ex)**  
  \<details>
  \<summary>클릭!\</summary>
  \<div markdown="1">
  까꿍
  \</div>
  \</details>
  - **result)**  
  <details>
  <summary>클릭!</summary>
  <div markdown="1">
  까꿍
  </div>
  </details>

---

# 버튼
  - **markdown ex)**  
  \<a href="#" class="click_button">Button\</a>
  - **result)**  
  <a href="#" class="click_button">Button</a>
  
  


  


