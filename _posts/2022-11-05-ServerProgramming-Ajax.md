---
title: "Ajax"
excerpt: "비동기 데이터 통신 기술"

categories:
- ServerProgramming

tags:
- [ServerProgramming]

toc: true
toc_sticky: true
toc_label: "Ajax"

last_modified_at: 2022-11-15T08:00:00-10:00:00
---

# 정의
  - Asynchronous Javascript And Xml
  - Javascript Library
  - 브라우저의 XMLHttpRequest 객체를 활용하여 페이지 새로고침 없이 데이터를 교환하고 조작하는 기법
  - 서버와 브라우저가 비동기 방식으로 데이터를 교환할 수 있는 통신기능

---

# Conventional Web Model <span style="color:gray">vs</span> Ajax Web Model
## Conventional Web Model
  ![image](/assets/images/ServerProgramming/Web_ConventionalModel.png)

## Ajax Web Model
  ![image](/assets/images/ServerProgramming/Web_AjaxModel.png)

---

# Ajax 장점
  - 페이지 이동 화면의 일부를 전환할수 있다.
  - 비동기 요청이 가능하다
  - 수신 데이터 양을 줄일 수 있다

# Ajax 단점
  - ajax를 지원하는 브라우저에서만 사용할 수 있다. (미지원 : 오페라 7 이하, IE 4.0 이하 등)
  - 페이지 이동 없는 통신으로 인한 보안상의 문제가 있을 수 있다.
  - 지원하는 charset이 한정되어 있다.

---

# ajax 적용

## XMLHttpRequest 객체 사용
  - 웹 브라우저에 내장된 XMLHttpRequest 객체를 사용

  ``` javascript
    var xMLHttpRequest = new XMLHttpRequest();
    // 요청에 대한 콜백 정의
    xMLHttpRequest.onreadystatechange = function() {
      if (xMLHttpRequest.readyState === xhr.DONE) {
        if (xMLHttpRequest.status === 200 || xMLHttpRequest.status === 201) {
          console.log(xMLHttpRequest.responseText);
        } else {
          console.error(xMLHttpRequest.responseText);
        }
      }
    };
    xMLHttpRequest.open('GET', url); // GET/POST 방식 과 url 전달
    xMLHttpRequest.send(); // 요청 전송
  ```

## jqeury
  - jquery 라이브러리 import 필요
  - XMLHttpRequest 불편함과 호환성 개선

  ```javascript
    $.ajax({
      url: 'url', // 요청이 전송될 URL 주소(필수)
      type: 'GET', // http 요청 방식 GET/POST (default: ‘GET’)
      async: true, // 요청 시 동기화 여부 (default:true)
      cache: true, // 캐시 사용 여부
      timeout: 3000, // Request Timeout (ms)
      data: { key: value }, // 요청 시 전달할 데이터
      contentType: 'application/json', // 요청 데이터 형식
      dataType: 'json', // 응답 데이터 형식 (명시하지 않을 경우 자동으로 추측)
      beforeSend: function() {
        // HTTP Request를 하기전에 호출.
      },
      success: function(data, status, xhr) {
        // 정상적으로 응답 받았을 경우에는 success 콜백이 호출
        // Param : 응답 바디, 응답 코드, XHR 헤더
      },
      error: function(xhr, status, error) {
        // 정상응답을 받지 못했을 경우 error 콜백이 호출
      },
      complete: function(xhr, status) {
        // success와 error 콜백이 호출된 후에 반드시 호출
      }
    })
  ```

## fetch API
  - 브라우저 내장 API
  - 가독성이 떨어지는 콜백함수 Syntax 개선 => Promise 방식 사용
  - 응답으로 Response 객체를 반환한다.
  - 구형 브라우저에서는 미지원
  
  ```javascript
    fetch('url', 설정)
      .then((response) => response.json())
      .catch((data) => console.log(data));
  ```

## Axios
  - 라이브러리 설치 필요
  - Node.js, React 환경에서 주로 사용
  - 가독성이 떨어지는 콜백함수 Syntax 개선 => Promise 방식 사용
  - 브라우저 호환성이 뛰어남
  - 자동으로 JSON 포맷 변환 지원

  ```javascript
    const axios = require('axios')

    axios
      .get('url')
      // 응답(성공)
      .then(function(response) {
        console.log(response);
      })
      // 응답(실패)
      .catch(function(error) {
        console.log(error);
      })
      // 응답(항상 실행)
      .then(function() {
        console.log("end");
      })
  ```
