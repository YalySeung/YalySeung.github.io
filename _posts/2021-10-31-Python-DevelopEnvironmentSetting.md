---
title: "Develop Environment Setting"
excerpt: "개발환경 셋팅"

categories:
  - Python

tags:
  - [Python]

toc: true
toc_sticky: true
toc_label: "Develop Environment Setting"

last_modified_at: 2022-02-04T08:00:00-10:00:00
---

# 파이썬 설치
  - 파이썬 다운로드 페이지 접속 [http://www.python.org\downloads]\(http://www.python.org\downloads)
  - ![image](/assets/images/Python/PythonDownloadMain.png){: width="70%" height="70%"}

    파일 다운로드
  - ![image](/assets/images/Python/PythonInstallWindow.png){: width="70%" height="70%"}

    셋업 실행

    PATH 등록 항목을 꼭 체크 하도록 하자~!

# VS Code에서 파이썬 사용하기
  - 확장 Utility 설치 :
    - ![image](/assets/images/Python/VSCodeExtentionPython.png){: width="70%" height="70%"}
      Pylance, Python
  - .py 파일 생성
  - 간단하게 로그파일에 로그를 쓰는 프로그램을 짜보았다.
    ```python
      import logging

      def create_logger():
        logger = logging.getLogger('myloger')
        formatter = logging.Formatter(u'%(asctime)s [%(levelname)8s] %(message)s')
        
        fileHandler = handlers.TimedRotatingFileHandler(filename='./History.log', when='midnight' ,interval=1, encoding='utf-8')
        fileHandler.setFormatter(formatter)
        fileHandler.suffix = "%Y%m%d"
        
        logger.addHandler(fileHandler)
        logger.setLevel(level=logging.INFO)
        logger.propagate = False
        return logger

      myLogger = create_logger()
      myLogger.info("#########LogWrite Start#########")
    ```
  - 실행
    - ![image](/assets/images/Python/PythonCompile.png){: width="70%" height="70%"}
  - 결과
    - ![image](/assets/images/Python/PythonLogWriteResult.png){: width="70%" height="70%"}
