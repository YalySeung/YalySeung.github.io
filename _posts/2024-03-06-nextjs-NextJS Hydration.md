---
title : "NextJS Hydration"
excerpt : "NextJS Hydration"
toc : true
toc_sticky : true
toc_label : "NextJS Hydration"
categories:
- NextJS
tags:
- [NextJS]
last_modified_at: 2024-03-06T08:00:00-10:00:00
---

# 날짜 : 2024-03-06 22:02

# 태그 : #NextJS
---

# 내용

## 정의
> **Hydration이란?**
>
> 정적 호스팅 혹은 SSR을 통해 받은 HTML 웹페이지를 동적인 웹페이지로 만드는 과정
{: .notice--info}

## Hydration Process
  
![image](../../assets/images/Hydration.png)
1. 사용자가 페이지를 요청
2. 브라우저는 서버에서 HTML 문서를 받아와 정적 페이지를 보여줌
3. 이와 동시에 Background에서는 HTML을 사용하여 React Component를 초기화
4. 생성된 React Component를 브라우저에 로드하여 동적 페이지를 보여줌

> **memo**
>
> Hydration 으로 HTML이 React Component로 교체되어, 사용자가 첫 화면부터 연속적이고 부드럽게 Rendering 되는 동적 웹페이지를 사용할 수 있다.
{: .notice}

> **memo**
>
> Hydration이 완료 되기 전에도 사용자는 정적 웹 페이지에서 컨텐츠를 확인 할 수 있다.
{: .notice}

---

# 연결문서
 - [CSR SSR](../../webcommon/webcommon-CSR-SSR)