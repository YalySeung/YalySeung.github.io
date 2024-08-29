---
title : "Multipart"
excerpt : "Multipart"
toc : true
toc_sticky : true
toc_label : "Multipart"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-01-16T08:00:00-10:00:00
---
  
---
  
## 정의
> **Multipart란?**  
>
> Client와 Server 간에 전송되는 HTTP 요청 또는 응답에서 여러 종류의 데이터 타입을 동시에 전송하기 위해 사용되는 데이터 포맷 
{: .notice--info}  
  
## 특징
- 일반적으로 파일 업로드와 관련된 데이터를 전송하는데 사용
- 파일 이진 데이터를 인코딩 하지 않고 원본 형식으로 전송
- Content-Type 헤더에 **multipart/form-data** 값을 가짐
- Multipart 형식의 데이터는 여러개의 part로 구성되며, 각 파트는 헤더와 본문으로 구성되어 있음
- 헤더에는 메타 데이터가 포함되어 있고, 본문에는 실제 데이터가 포함됨
  
## 예시
  
### Multipart Request
  
#### MultipartEntityBuilder 와 HttpPost를 사용한 방식
  
```java
private void sendRequest(RequestData requestData, File file) throws IOException {  
    MultipartEntityBuilder entityBuilder = MultipartEntityBuilder.create();  
    entityBuilder.addTextBody("usage", "Y");  
    entityBuilder.addTextBody("name", requestData.getAge(), ContentType.create("text/plain", StandardCharsets.UTF_8));  
    entityBuilder.addTextBody("age", String.valueOf(RequestData.getName())); 
    entityBuilder.addBinaryBody("file", file, ContentType.DEFAULT_BINARY, file.getName());  
  
    HttpPost request = new HttpPost("http://test.com:8080/regist");  
    request.setEntity(entityBuilder.build());  
  
    try (CloseableHttpClient httpClient = HttpClients.createDefault();  
         CloseableHttpResponse response = httpClient.execute(request)) {  
        // Handle the response  
        String responseBody = EntityUtils.toString(response.getEntity());  
    }  
}
```
  
### Endpoint
  
```java
@PostMapping("/regist")  
public ResponseEntity<BaseResponse> registerUser(@Valid registerUserRequest request, BindingResult bindingResult) {  
    return new ResponseEntity<BaseResponse>(userService.regist(request), HttpStatus.OK);
```
  
### Multipart 파일 처리
  
```java
public String write(MultipartFile multipartFile, String subPath, String fileName) throws IOException {  
    String filePath = createFilePath(subPath, fileName);  
    createIfParentsDirNotExists(repositoryPath + filePath, fileName);  
    writeMultipartFile(multipartFile, repositoryPath, filePath);  
    return filePath;  
}

private void writeMultipartFile(MultipartFile multipartFile, String rootPath, String filePath)  
        throws IllegalStateException, IOException {  
    Assert.notNull(multipartFile, "file must not be null");  
    Assert.isTrue(multipartFile.getSize() > 0, "size must be greater than 0");  
    File targetFile = new File(rootPath + SEPARATOR + filePath);  
    multipartFile.transferTo(targetFile);  
}
```
  
## Multipart RawData Example
  
```http
POST http://61.109.169.41:7200/rpa/webadmin/publicfile/register HTTP/1.1
Host: 61.109.169.41:7200
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryXPLfucybaRfnOC6m
Origin: http://61.109.169.41:7200
...

------WebKitFormBoundaryXPLfucybaRfnOC6m
Content-Disposition: form-data; name="file"; filename="image (1).png"
Content-Type: image/png

//바이너리 데이터 body

------WebKitFormBoundaryXPLfucybaRfnOC6m
Content-Disposition: form-data; name="useExpiryDate"
20240215
------WebKitFormBoundaryXPLfucybaRfnOC6m
Content-Disposition: form-data; name="useScopeCode"
GROUP
------WebKitFormBoundaryXPLfucybaRfnOC6m
Content-Disposition: form-data; name="readOnlyYn"
Y
------WebKitFormBoundaryXPLfucybaRfnOC6m
Content-Disposition: form-data; name="useYn"
Y
------WebKitFormBoundaryXPLfucybaRfnOC6m--
```

> **tip**
>
> 라이브러리를 사용하여 Multipart 요청을 보낼수도 있지만 위와같은 포맷의 데이터를 만들어서 전송하기도 한다. 
{: .notice--info}  

---
  
# 연결문서
