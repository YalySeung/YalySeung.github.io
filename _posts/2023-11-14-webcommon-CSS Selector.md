---
title : "CSS Selector"
excerpt : "CSS Selector"
toc : true
toc_sticky : true
toc_label : "CSS Selector"
categories:
- WebCommon
tags:
- [FrontEnd, WebCommon]
last_modified_at: 2023-11-14T08:00:00-10:00:00
---
  
---
  
## CSS Selector
  
### \*
- 전체 요소 대상
- 브라우저에 과부하
  
### \#
- id와 일치하는 요소를 대상
  
### .\<Class명\> 
{: .notice}  
- class 가 일치하는 요소를 대상
  
### \<요소명\> 
{: .notice}  
- 요소명이 일치하는 요소를 대상
  
### \<요소명\> \<자식 요소명\> 
{: .notice}  
- 요소의 자식요소중 일치하는 자식요소를 대상
  
### \<요소명\>:\<Class명\> 
{: .notice}  
- 요소의 Class가 일치하는 요소를 대상
  
### \<요소명1\> \> \<요소명2\> 
{: .notice}  
- 요소명1 의 직계 요소명2 요소를 대상
  
### 형제 요소 선택
  
#### \<요소명1\> + \<요소명2\> 
{: .notice}  
- 요소명1 바로 뒤의 요소명2를 대상
  
#### \<요소명1\> ~ <요소명2> 
{: .notice}  
- [<요소명1 > + <요소명2 >](#요소명1---요소명2-)와 유사하지만 덜 엄격 
{: .notice}  
- 요소명1의 모든 자식 요소명2 요소를 대상
  
### \<요소명\>\[\<tag명>\] 
{: .notice}  
- tag를 포함한 요소를 대상
  
### \<요소명\>\[href=\<url\>\] 
{: .notice}  
- 해당 href 링크를 포함한 요소를 대상
  
### <요소명>:checked 
{: .notice}  
- 라디오, 체크박스 처럼 에크가 가능한 요소들을 대상
  
### <요소명>:before 
{: .notice}  
- 요소 앞에 가상요소 추가
  
```css
.div:before {
    content: "";
    display: block;
    clear: both;
    visibility: hidden;
    font-size: 0;
    height: 0;
    }
```
  
### <요소명>:after 
{: .notice}  
- 요소 뒤에 가상요소 추가
  
```css
.div:after {
    content: "";
    display: block;
    clear: both;
    visibility: hidden;
    font-size: 0;
    height: 0;
    }
```
  
### <요소명>:hover 
{: .notice}  
- 해당 요소에 커서를 올릴때, 스타일 적용
  
### <요소명>:not() 
{: .notice}  
- 요소 중 특정 요소만 제거
  
```css
div:not(#container) {
   color: blue;
}
```
  
### <요소명>::가상 요소 
{: .notice}  
  
#### <요소명>::first-line 
{: .notice}  
- 요소의 첫줄에만 적용
  
```css
p::first-line {
   font-weight: bold;
   font-size: 1.2em;
}
```
  
#### <요소명>::first-letter 
{: .notice}  
- 요소의 첫글자에만 적용
  
```css
p::first-letter {
   float: left;
   font-size: 2em;
   font-weight: bold;
   font-family: cursive;
   padding-right: 2px;
}
```
  
### <요소명>:nth-child(\<index\>) 
{: .notice}  
- 요소의 index번째 요소를 대상
  
### <요소명>:nth-last-child(\<index\>) 
{: .notice}  
- 요소의 뒤에서 index번째 요소를 대상
  
### <요소명>:nth-of-type(\<index\>) 
{: .notice}  
- 요소의 type이 일치하는 요소를 대상
  
### <요소명>:first-child 
{: .notice}  
- 요소의 첫번째 자식요소를 대상
- 맨 처음과 맨 마지막 테두리 선을 제거할때 많이 사용
  
### <요소명>:last-child 
{: .notice}  
- 요소의 마지막 자식 요소를 대상

---
  
# 연결문서
- [html-tags](../../webcommon/webcommon-html-tags)
- [html-작성법 기본](../../webcommon/webcommon-html-작성법-기본)