---
title : "DNS"
excerpt : "DNS"
toc : true
toc_sticky : true
toc_label : "DNS"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2023-11-20T08:00:00-10:00:00
---
  
---
  
> **DNS란?**  
>
>Domain Name System의 약어로 Domain 이름을 컴퓨터가 이해할 수 있는 숫자로 된 IP로 바꾸는 역할을 하는 서비스이다. 
{: .notice--info}  
  
## DNS의 주요 기능
  DNS는 사용자가 웹 브라우저에 도메인 명을 입력하면, 해당 **도메인 이름을 IP 주소로 변환**하여 사용자가 원하는 웹사이트에 접속할 수 있도록 도와준다. 
  DNS는 **계층적 구조**를 가지고 있어, www.example.com 에서 'com'은 최상위 도메인, 'example'은 서브도메인, 'www'는 호스트 명을 의미한다.
  DNS의 **데이터베이스**는 **전 세계 여러 서버에 분산되어 저장**된다. 이는 중앙 집중형 시스템의 단일 장애점 문제를 피하고, 데이터 조회를 효율적으로 만든다. 
  
## DNS의 작동 과정
  
![image](../../assets/images/DNDSWorkflow.png)

 1. 사용자가 브라우저에 도메인을 입력하면 브라우저는 **Local DNS**서버 에 IP 주소를 요청한다.
 2. Local DNS서버에 IP 정보가 없을 경우 **Root DNS**서버로 DNS Query를 전달한다.
 3. Root DNS서버에 IP 정보가 있다면 바로 브라우저로 전달한다.
 4. Root DNS서버에 IP 정보가 없다면 **com DNS**서버에 IP 정보를 요청한다.
 5. com DNS서버에 IP 정보가 있다면 바로 브라우저로 전달한다.
 6. com DNS서버에 IP 정보가 없다면 **Authoritative DNS** 서버에 직접 IP정보를 요청한다.
 7. Auhoritative DNS서버는 IP정보를 Local DNS서버로 전달한다.
 8. Local DNS서버는 전달 받은 IP 정보를 브라우저에 전송한다.
 9. 브라우저는 전달받은 IP로 Google 서버에 페이지를 요청한다.
 10. 사용자에게 페이지가 보여진다.

 이렇게 IP 정보를 찾는 과정을 재귀적 쿼리(Recursive Query)라고 부른다.

> **Local DNS서버란?**  
>
> KT, SK 브로드밴드, LG 유플러스 등 의 Internet Service Provider 의 기지국 DNS 서버를 뜻한다. 
{: .notice--info}  

> **Root DNS서버란?**  
>
> 인터넷의 도메인 네임 시스템의 루트 존을 뜻한다. ICANN이 직접 관리하는 서버로, TLD DNS 서버 IP들을 저장해두고 안내하는 역할을 한다. 
{: .notice--info}  

> **TLD DNS 서버란**  
>
> Top-Level Domain 서버로 도메인 등록 기관에서 관리하는 서버이다. .com 이나 .co.kr 같은 도메인들을 관리하고 부여하는 역할을 한다. 
{: .notice--info}  

> **com DNS서버란?**  
>
> com 도메인을 관리하는 TLD DNS서버이다. 
{: .notice--info}  

> **Authoritative DNS 서버란?**  
>
> 실제 개인 도메인과 IP 주소의 관계가 기록/저장/변경되는 서버로 일반적으로 도메인/호스팅 업체의 네임버서를 말하지만, 개인이나 회사 DNS 서버를 의미하기도 한다. 
{: .notice--info}  

---
  
# 연결문서
- [DDNS](../../servercommon/servercommon-DDNS)
- [ISP](../../통신/통신-ISP)