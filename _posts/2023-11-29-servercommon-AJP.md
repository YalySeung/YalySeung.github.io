---
title : "AJP"
excerpt : "AJP"
toc : true
toc_sticky : true
toc_label : "AJP"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2023-11-29T08:00:00-10:00:00
---
  
---
  
## 📌 AJP란?

> **info**
>
> AJP는 Apache JServ Protocol의 약자로, **웹 서버와 애플리케이션 서버 간의 효율적인 통신을 위한 바이너리 프로토콜**이다.  
> HTTP 기반보다 **더 빠르고 가벼운 통신**을 지원하며, 주로 **Apache HTTP Server ↔ Tomcat** 간 연동에 사용된다. 
{: .notice--info}  

---
  
## ✅ AJP의 특징

- **이진(Binary) 프로토콜** 기반으로 HTTP보다 빠름
- 프록시 연결 시 **최적화된 성능 제공**
- 기본 포트는 **8009**
- **헤더 필터링, 요청 포워딩, 세션 연동** 등에 적합

---
  
## ✅ mod_jk란?

> **info**
>
> `mod_jk`는 Apache HTTP Server와 Tomcat을 AJP 프로토콜을 이용하여 연결하기 위한 모듈이다. 
{: .notice--info}  
  
### 🔹 주요 기능

- AJP 포트를 통해 요청을 Tomcat으로 위임
- Apach 설정만으로 웹과 WAS 간 요청 분리 가능
- Tomcat은 별도의 HTTP 포트를 사용하지 않아도 됨

---
  
## ✅ mod_jk 동작 방식

1. Apache 웹서버의 `httpd.conf` 또는 `workers.properties`에 Tomcat 연동 설정 추가
2. 사용자가 Apache(80 port)에 접속하여 요청
3. Apache는 요청 URL이 Tomcat으로 위임되어야 하는지 확인
4. 위임 대상인 경우, **AJP 포트(기본: 8009)** 를 통해 Tomcat에 요청 전달
5. Tomcat은 처리 결과를 다시 Apache로 반환
6. Apache는 사용자에게 최종 응답 반환

---
  
## ✅ AJP 사용 시 주의점

- **보안**: AJP는 내부 통신용이므로 외부 노출 시 위험 → `secret`, `allowedRequestAttributesPattern` 설정 권장
- **역할 분리**: 정적 리소스는 Apache가 처리, 동적 요청은 Tomcat이 담당
- **성능 조정**: worker 프로퍼티를 통한 connection 수, timeout 설정 등 필요

---
  
## ✅ 대체 기술

| 방식 | 설명 |
|------|------|
| mod_proxy_ajp | Apache에서 AJP를 사용해 Tomcat과 연결 |
| mod_proxy_http | AJP 대신 HTTP로 프록시 연결 |
| Nginx + HTTP | AJP 없이 Nginx에서 HTTP 기반 프록시 사용 |

---
  
# 연결문서
- [Port](../../developcommon/developcommon-Port)
- [ApacheAndTomcat](../../servercommon/servercommon-ApacheAndTomcat)
- [Proxy서버](../../webcommon/webcommon-Proxy서버)
