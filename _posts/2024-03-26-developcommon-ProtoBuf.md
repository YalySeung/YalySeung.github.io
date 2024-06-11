---
title : "ProtoBuf"
excerpt : "ProtoBuf"
toc : true
toc_sticky : true
toc_label : "ProtoBuf"
categories:
- DevelopCommon
tags:
- [DevelopCommon]
last_modified_at: 2024-03-26T08:00:00-10:00:00
---
  
---
  
## 정의
> **ProtoBuf란?**  
>
> Protocol Buffers
> Google에서 개발한 데이터 직렬화 형식. 
> 
>  
{: .notice--info}  
  
## 장점
- 시스템 간의 데이터 스트림을 사용하는 API를 만드는데 사용 가능
- **응용프로그램 간 RPC 통신에 사용 가능 (Interface의 DataType 정의 가능)**
- 데이터가 변경될 때, 이전 버전화 호환성 보장
- 구조화된 데이터는 바이너리 형식으로 저장되어 XML, JSON 형식과 같은 텍스트 기반 형식보다 네트워크 전송이 빠름
  
## .proto 파일의 compile
  
### compiler 다운로드
- [ProtoBuf 다운로드 링크](https://github.com/protocolbuffers/protobuf/tags)
  
### 컴파일러 경로로 이동하여 .proto 파일 실행
- proto.exe --\<언어타입\>_out=\<output 경로\> \<.proto 파일 경로\> 
{: .notice--info}  

> **example**
>
> protoc.exe --csharp_out=./ C:\WorkSpace\Server\Protoc\protoc-23.3-win64\include\MyProto.proto 
{: .notice}  
  
### output 경로에 생성된 파일 확인

---
  
# 연결문서
