---
title : "HTTP Request Smuggling"
excerpt : "HTTP Request Smuggling"
toc : true
toc_sticky : true
toc_label : "HTTP Request Smuggling"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2023-12-25T08:00:00-10:00:00
---
  
---
  
## 정의
> **HTTP Request Smuggling이란?**  
>
> 사용자로부터 수신된 HTTP 요청 순차 처리를 방해하는 기술 
{: .notice--info}  
  
## 특징
- WAS 의 취약점을 이용해 보안 장치를 우회할 수 있고 인가되지 않은 민감한 데이터를 접근할 수 있으며, 직접적으로 다른 사용자들에게 손해를 줄 수 있음 
  
## HTTP Request Smuggling 취약점
- front-end 서버가 back-end 서버에 HTTP 요청을 보낼때, 효율성을 위해 한번 연결된 3-way-handshacke 를 통해 여러개의 요청을 보냄
- 이런 요청은 차례대로 전송되므로 back-end 서버는 요청의 시작과 끝을 인식하기 위해 [HTTP Request Header](../../servercommon/servercommon-HTTP-Request#entity-헤더)를 분석
- back-end 서버는 요청패킷의 chunked 또는 Content-Length 를 만나면 지정된 데이터만큼 처리하고 나머지 패킷은 버퍼에 잠시 남겨둔다.
- 버퍼에 남은 데이터는 다음 요청의 시작으로 처리된다.
  
### Request Sample
  
```HTTP
POST /search HTTP/1.1 
Host: samplehost.com 
Content-Type: application/x-www-form-urlencoded 
Content-Length: 11 

<11자리의 Data><Smuggling 공격을 할 Data> 
{: .notice--info}  
```

> **note**
>
> 여기서 주목해야 할 점은 Header에 명시된 Content  이외에 Smuggling 공격에 사용할 data를 Body에 포함시켰다는 것이다. 
{: .notice}  

---
  
# 연결문서
- [HTTP Request](../../servercommon/servercommon-HTTP-Request#entity-헤더)