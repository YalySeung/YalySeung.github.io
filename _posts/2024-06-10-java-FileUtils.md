---
title : "FileUtils"
excerpt : "FileUtils"
toc : true
toc_sticky : true
toc_label : "FileUtils"
categories:
- java
tags:
- [Java]
last_modified_at: 2024-06-10T08:00:00-10:00:00
---
  
---
  
 **FileUtils** 는 Apache Commons IO 라이브러리로 **파일 및 디렉토리 작업**을 간편하게 수행할 수 있도록 다양한 **유틸리티 메서드**를 제공한다. 
  
## 주요 메서드
 FileUtils에서 자주 사용하는 유용한 메서드를 살펴보자.

| 메서드명                                                                       | 기능                          |
| -------------------------------------------------------------------------- | --------------------------- |
| copyFile(File srcFile, File destFile)                                      | 파일을 복사한다.                   |
| copyFileToDirectory(File srcFile, File destDir)                            | 파일을 디렉토리로 복사한다.             |
| copyDirectory(File srcDir, File destDir)                                   | 디렉토리를 복사한다.                 |
| moveFile(File srcFile, File destFile)                                      | 파일을 이동한다.                   |
| moveFileToDirectory(File srcFile, File destDir, boolean createDestDir)     | 파일을 디렉토리로 이동한다.             |
| moveDirectory(File srcDir, File destDir)                                   | 디렉토리를 이동한다.                 |
| moveDirectoryToDirectory(File srcDir, File destDir, boolean createDestDir) | 디렉토리를 다른 디렉토리로 이동한다.        |
| deleteQuietly(File file)                                                   | 파일 또는 디렉토리를 삭제한다.           |
| forceDelete(File file)                                                     | 파일 또는 디렉토리를 강제로 삭제한다.       |
| readFileToString(File file, Charset encoding)                              | 파일을 문자열로 읽는다.               |
| writeStringToFile(File file, String data, Charset encoding)                | 문자열을 파일에 쓴다.                |
| readLines(File file, Charset encoding)                                     | 파일을 라인별로 읽어 리스트로 반환한다.      |
| forceMkdir(File directory)                                                 | 상위 디렉토리를 포함한 모든 디렉토리를 생성한다. |  

 경로를 Handling 하다보면 **Path** 객체를 사용하게 되는데, FileUtils API 는 거의다 **File 타입 인자**를 필요로하므로 **Path.toFile() 메서드를 사용하여 변환**하자.
 
---
  
# 연결문서
