---
title : "RequestBodyLogging"
excerpt : "RequestBodyLogging"
toc : true
toc_sticky : true
toc_label : "RequestBodyLogging"
categories:
- Spring
tags:
- [Spring, Servlet, Filter]
last_modified_at: 2025-06-09T08:00:00-10:00:00
---
  
---
  
## ✅ 고급 활용: 요청/응답 로깅 필터

Spring 환경에서 `HttpServletRequest`와 `HttpServletResponse`를 **래핑(wrap)** 하여 **본문 읽기 및 로깅**이 가능하다.

- 요청 래핑: `CachedBodyHttpServletRequest`
- 응답 래핑: `CustomResponseWrapper`
- multipart 여부 체크: `CustomMultipartResolver`
- JSON 파싱 및 로깅: `JsonParser`, `BaseResponse` 활용
  
```java
@Component
@Order(Ordered.LOWEST_PRECEDENCE)
public class RequestResponseLoggingFilter implements Filter {

    private static final Logger logger = LoggerFactory.getLogger(RequestResponseLoggingFilter.class);

    @Autowired
    CustomMultipartResolver customMultipartResolver;

    @Override
    public void init(FilterConfig filterConfig) throws ServletException {
    }

    @Override
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain)
            throws IOException, ServletException {
        HttpServletRequest httpServletRequest = (HttpServletRequest) request;
        HttpServletResponse httpServletResponse = (HttpServletResponse) response;

        HttpServletRequest wrapperRequest = loggingRequest(httpServletRequest);

        CustomResponseWrapper customResponseWrapper = new CustomResponseWrapper(httpServletResponse);

        chain.doFilter(wrapperRequest, customResponseWrapper);

        loggingResponse(customResponseWrapper);
    }

    private void loggingResponse(CustomResponseWrapper customResponseWrapper) {
        StringBuilder responseLogBuilder = new StringBuilder();

        responseLogBuilder.append("\n===**[API Response]**===\n");
        responseLogBuilder.append("[StatusCode] = " + customResponseWrapper.getStatus() + "\n");
        String responseContentType = customResponseWrapper.getContentType();
        if (StringUtils.hasText(responseContentType)
                && responseContentType.startsWith(MediaType.APPLICATION_JSON_VALUE)) {
            String responseBody = customResponseWrapper.getCaptureAsString();

            try {
                if (StringUtils.hasText(responseBody)) {
                    BaseResponse baseResponse = JsonParser.toObject(responseBody, BaseResponse.class);
                    responseLogBuilder.append("[isSuccess] = " + baseResponse.getIsSuccess() + "\n");
                    responseLogBuilder.append("[errorCode] = " + baseResponse.getErrorCode() + "\n");
                    responseLogBuilder.append("[errorMessage] = " + baseResponse.getErrorMessage() + "\n");
                } else {
                    responseLogBuilder.append("[isSuccess] = true\n");
                }
            } catch (Exception ex) {
            }
        }

        logger.info(responseLogBuilder.toString());
    }
}

```
  
---
  
### ✅ 1. CachedBodyServletInputStream.java
  
```java
package com.testsystem.filter;

import java.io.ByteArrayInputStream;
import javax.servlet.ReadListener;
import javax.servlet.ServletInputStream;
import java.io.IOException;

public class CachedBodyServletInputStream extends ServletInputStream {

    private final ByteArrayInputStream byteArrayInputStream;

    public CachedBodyServletInputStream(ByteArrayInputStream byteArrayInputStream) {
        super();
        this.byteArrayInputStream = byteArrayInputStream;
    }

    @Override
    public boolean isFinished() {
        return this.byteArrayInputStream.available() == 0;
    }

    @Override
    public boolean isReady() {
        return true;
    }

    @Override
    public void setReadListener(ReadListener readListener) {
        throw new UnsupportedOperationException();
    }

    @Override
    public int read() throws IOException {
        return byteArrayInputStream.read();
    }
}
```

---
  
### ✅ 2. CustomResponseWrapper.java
  
```java
package com.testsystem.filter;

import java.io.CharArrayWriter;
import java.io.PrintWriter;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.http.HttpServletResponseWrapper;

public class CustomResponseWrapper extends HttpServletResponseWrapper {

    private final CharArrayWriter charArrayWriter = new CharArrayWriter();
    private final PrintWriter printWriter = new PrintWriter(charArrayWriter);

    public CustomResponseWrapper(HttpServletResponse response) {
        super(response);
    }

    @Override
    public PrintWriter getWriter() {
        return printWriter;
    }

    public String getCaptureAsString() {
        printWriter.flush();
        return charArrayWriter.toString();
    }
}
```

---
  
### ✅ 3. CachedBodyHttpServletRequest.java
  
```java
package com.testsystem.filter;

import java.io.ByteArrayInputStream;
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import javax.servlet.ServletInputStream;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletRequestWrapper;
import org.springframework.util.StreamUtils;

public class CachedBodyHttpServletRequest extends HttpServletRequestWrapper {

    public final byte[] cachedBody;

    public CachedBodyHttpServletRequest(HttpServletRequest request) throws IOException {
        super(request);
        this.cachedBody = StreamUtils.copyToByteArray(request.getInputStream());
    }

    @Override
    public ServletInputStream getInputStream() throws IOException {
        return new CachedBodyServletInputStream(new ByteArrayInputStream(cachedBody));
    }

    public String getCachedBody() {
        return new String(cachedBody, StandardCharsets.UTF_8);
    }
}
```

---
  
### ✅ 4. CachedBodyMultipartHttpServletRequest.java
  
```java
public class CachedBodyMultipartHttpServletRequest extends HttpServletRequestWrapper
        implements MultipartHttpServletRequest {

    private final MultipartHttpServletRequest multipartHttpServletRequest;

    public CachedBodyMultipartHttpServletRequest(MultipartHttpServletRequest request) {
        super(request);
        this.multipartHttpServletRequest = request;
    }

    @Override
    public Iterator<String> getFileNames() {
        return multipartHttpServletRequest.getFileNames();
    }

    @Override
    public MultipartFile getFile(String name) {
        return multipartHttpServletRequest.getFile(name);
    }

    @Override
    public List<MultipartFile> getFiles(String name) {
        return multipartHttpServletRequest.getFiles(name);
    }

    @Override
    public Map<String, MultipartFile> getFileMap() {
        return multipartHttpServletRequest.getFileMap();
    }

    @Override
    public MultiValueMap<String, MultipartFile> getMultiFileMap() {
        return multipartHttpServletRequest.getMultiFileMap();
    }

    @Override
    public String getMultipartContentType(String paramOrFileName) {
        return multipartHttpServletRequest.getMultipartContentType(paramOrFileName);
    }

    @Override
    public HttpMethod getRequestMethod() {
        return multipartHttpServletRequest.getRequestMethod();
    }

    @Override
    public HttpHeaders getRequestHeaders() {
        return multipartHttpServletRequest.getRequestHeaders();
    }

    @Override
    public HttpHeaders getMultipartHeaders(String paramOrFileName) {
        return multipartHttpServletRequest.getMultipartHeaders(paramOrFileName);
    }
}
```

---
  
## 🔄 연결 구성도

```
[Client]
  ↓
RequestResponseLoggingFilter
  ↓
(CachedBodyHttpServletRequest or CachedBodyMultipartHttpServletRequest)
  ↓
Controller 처리
  ↓
(CustomResponseWrapper 로 응답 내용 로깅)
```

---
  
# 연결문서
- [Filter](../../spring/spring-Filter)