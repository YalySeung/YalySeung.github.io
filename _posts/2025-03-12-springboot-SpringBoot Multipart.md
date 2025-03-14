---
title : "SpringBoot Multipart"
excerpt : "SpringBoot Multipart"
toc : true
toc_sticky : true
toc_label : "SpringBoot Multipart"
categories:
- SpringBoot
tags:
- [SpringBoot]
last_modified_at: 2025-03-12T08:00:00-10:00:00
---
  
---
  
> **Spring Boot에서 Multipart Request 처리란?**  
>
>  파일 업로드를 포함한 다중 데이터 요청을 처리하기 위한 방법을 의미한다. 
{: .notice--info}  

  Spring Boot에서는 **`MultipartFile`을 활용하여 간편하게 파일 업로드를 처리할 수 있으며, 커스텀 `MultipartResolver`를 통해 요청을 제어할 수도 있다.**
  
## Multipart Resolver 설정
  
### 1️⃣ 기본 설정 (`application.properties`)
  
```properties
spring.servlet.multipart.enabled=true
spring.servlet.multipart.max-file-size=10MB
spring.servlet.multipart.max-request-size=50MB
```
  
### 2️⃣ 커스텀 `MultipartResolver` 구현
  
```java
package com.imagesystem.config;

import java.util.Locale;
import org.springframework.stereotype.Component;
import org.springframework.web.multipart.MultipartException;
import org.springframework.web.multipart.MultipartFile;
import org.springframework.web.multipart.MultipartResolver;
import org.springframework.web.multipart.commons.CommonsMultipartResolver;
import org.springframework.util.StringUtils;

@Component
public class CustomMultipartResolver extends CommonsMultipartResolver implements MultipartResolver {

    @Override
    protected MultipartParsingResult parseRequest(HttpServletRequest request) throws MultipartException {
        MultipartParsingResult parsingResult = super.parseRequest(request);
        try {
            Map<String, String> parameterMap = parsingResult.getMultipartParameterContentTypes();

            for (String key : parameterMap.keySet()) {
                if (!StringUtils.hasText(parameterMap.get(key))) {
                    String value = parsingResult.getMultipartParameters().get(key)[0];

                    if (StringUtils.hasText(value) && (value.startsWith("{") || value.startsWith("["))) {
                        parameterMap.put(key, MediaType.APPLICATION_JSON_VALUE);
                    } else {
                        parameterMap.put(key, MediaType.MULTIPART_FORM_DATA_VALUE);
                    }
                }
            }

            return new MultipartParsingResult(parsingResult.getMultipartFiles(),
                    parsingResult.getMultipartParameters(), parameterMap);

        } catch (MultipartException ex) {
            throw new ApiException(ApiError.INVALID_PARAMETER, "multipart 데이터 처리 실패 message : " + ex.getMessage());
        }
    }

    @Override
    public boolean isMultipart(HttpServletRequest request) {
        String contentType = request.getContentType();
        if (contentType != null && contentType.toLowerCase(Locale.ENGLISH).startsWith(FileUploadBase.MULTIPART)) {
            return true;
        }
        return super.isMultipart(request);
    }
}
```
  
## Multipart 처리 예제
  
### 3️⃣ 파일 업로드 Controller
  
```java
import org.springframework.web.bind.annotation.*;
import org.springframework.web.multipart.MultipartFile;

@RestController
@RequestMapping("/upload")
public class FileUploadController {

    @PostMapping
    public String handleFileUpload(@RequestParam("file") MultipartFile file) {
        return "Uploaded file: " + file.getOriginalFilename();
    }
}
```
  
## 장점과 단점
  
### ✅ 장점
- **Spring Boot에서 기본적으로 Multipart 지원 제공**  
- **간단한 설정만으로 파일 업로드 기능 구현 가능**  
  
### ❌ 단점
- **파일 크기 제한 설정을 명확히 하지 않으면 예외 발생 가능**  
- **파일 저장 및 보안 관련 추가적인 설정 필요**  

---
  
# 연결문서
- [Multipart](../../servercommon/servercommon-Multipart)
