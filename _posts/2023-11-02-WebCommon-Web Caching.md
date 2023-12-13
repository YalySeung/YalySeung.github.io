---
title : "Web Caching"
excerpt : "Web Caching"
toc : true
toc_sticky : true
toc_label : "Web Caching"
categories:
- WebCommon
tags:
- [WebCommon]
last_modified_at: 2023-11-02T08:00:00-10:00:00
---

# 날짜 : 2023-11-02 11:09

# 태그 : #WebCommon
---

# 내용
  
![image](../../assets/Images/WebCaching.png)

## 기능
- 사용자가 웹사이트에 접속할 때, 정적 컨텐츠(js, 이미지, css)를 특정 위치에 저장하여, 웹 사이트 서버에 해당 컨텐츠를 저장
- 저장 후 웹 사이트에 다시 접속할 경우, 저장된 위치에서 정적 컨텐츠를 불러와 서버 응답 시간을 줄이고, 서버의 트래픽을 감소시킴

## 종류

### Service Worker Cache
- 캐시 스토리지 API 사용시, 브라우저 캐시를 참조하기 전에 Service Worker 에서 HTTP 요청을 가로채고 캐싱 전략에 따라 Service Worker 내 데이터를 먼저 사용
- 워커의 일종으로 백그라운드에서 비동기적으로 실행되는 자바스크립트
- 보안상의 이유로 https에서만 사용 가능
- 동기적 XHR이나 웹 스트리지 접근 불가능
- 캐시 스토리지 API 제공

### Browser Caches
- 모든 HTTP 요청은 서버로 직접 요청을 보내지 않고 Browser Cache로 라우팅 되며, 필요한 데이터가 존재한다면 Browser Cache 데이터를 사용한다.
- 브라우저 또는 HTTP 요청을 하는 Client Application에 의해 내부 디스크 또는 메모리에 저장되는 캐시
- 클라이언트 간 공유 불가능
- 브라우저의 back, 페이지 재방문시, 서비스 효율 증가

### Proxy Caches([CDN](../../WebCommon/WebCommon-CDN))
- Browser Cache와 동일한 원리로 동작
- 네트워크상에서 동작
- 주로 [IPS](../../ServerCommon/ServerCommon-IPS)의 방화벽에 설치
- 대기시간, 트래픽 감소
- 접근정책과 제한 우회, 사용률 기록
- 한정된 수의 클라이언트를 위해 다수의 웹 서버 컨텐츠를 캐시

## HTML 헤더에서 캐시속성

### HTTP Request

#### cache-control

|디렉티브|설명|
|---|---|
|no-cache|응답으로 받은 데이터를 캐싱하되, 매번 서버에 요청하여 해당 데이터에 대한 유효성 검증 실행|
|no-store|캐싱 안함|
|no-transform|캐싱할 데이터에 대해 압축이나 포맷 지원 X|
|only-if-cache|캐시된 데이터가 있을 경우에만 반환|
|max-age|현재시점 기준 캐시 유효시간|
|max-stale|캐시된 데이터가 있다면 만료된 이후에도 지정한 시간동안 사용가능|
|min-fresh|캐시된 데이터가 변경되지 않아야할 최소 시간|

### HTTP Response

#### cache-control

|디렉티브|설명|
|---|---|
|public|[CDN](../../WebCommon/WebCommon-CDN) 이나 프록시 서버 같은 공용 캐시에서도 캐싱 허용|
|private|브라우저 캐시등의 로컬 캐시에서만 캐싱 가능|
|must-revalidate|캐시된 데이터를 사용하기 전 반드시 서버에게 유효성 검사|
|proxy-revalidate|must-revalidate + 공유 캐시에만 적용|
|no-cache|응답으로 받은 데이터를 캐싱하되, 매번 서버에 요청하여 해당 데이터에 대한 유효성 검증 실행|
|no-store|캐싱 안함|
|no-transform|캐싱할 데이터에 대해 압축이나 포맷 지원 X|
|max-age|현재시점 기준 캐시 유효시간|
|s-maxage|max-age + 공유 캐시에만 적용|

#### Expires

|디렉티브|설명|
|---|---|
|http-date(timestamp)|지정한 날짜 및 시간까지만 캐싱된 데이터가 유효|
|etc|캐시된 데이터가 유효하지 않음|

#### E-tag
- 리소스가 업데이트 되었는지 확인하는데 사용하는 값

#### Last-Modified
- 마지막으로 수정된 시간 기록 및 비교
- 브라우저가 이전에 요청했던 Last-Modified 를 If-Modified-Since 속성으로 함께 전달

---

# 연결문서
- [CDN](../../WebCommon/WebCommon-CDN) 