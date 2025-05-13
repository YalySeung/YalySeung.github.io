---
title : "python 프로젝트"
excerpt : "python 프로젝트"
toc : true
toc_sticky : true
toc_label : "python 프로젝트"
categories:
- python
tags:
- [Python]
last_modified_at: 2025-03-27T08:00:00-10:00:00
---
  
---
  
> **파이썬 프로젝트 환경 설정 및 배포**  
>
> 파이썬 개발 환경 구축부터 프로젝트 패키징 및 배포까지의 기본 과정을 안내한다. 
{: .notice--info}  

---
  
## 📌 파이썬 설치
[파이썬 공식 사이트](https://www.python.org/)에서 최신 버전 설치

---
  
## 📌 환경변수 설정
- 파이썬 설치 경로를 시스템 PATH에 추가
- Windows 예시: `내 컴퓨터` → `속성` → `고급 시스템 설정` → `환경 변수`

---
  
## 📌 VSCode 확장 설치
- Python
- Pylance
- autopep8
- Python Test Explorer for Visual Studio Code

---
  
## 📌 필수 패키지 설치 (`setuptools`)
  
```bash
pip install setuptools
```

---
  
## 📌 프로젝트 패키징 및 배포 과정
  
### 🎯 패키지 설치 (로컬 설치)
  
```bash
python setup.py install
```
  
### 🎯 Source Distribution 생성
  
```bash
python setup.py sdist
```

생성된 파일 설치
  
```bash
pip install dist/your_project_name-1.0.0.tar.gz
```
  
### 🎯 개발 모드로 설치 (편집 가능 모드)
  
```bash
pip install -e .
```

---
  
## 📌 패키지 배포 (PyPI 공개)
  
### 🎯 Twine 설치
  
```bash
pip install twine
```
  
### 🎯 PyPI 배포
  
```bash
twine upload dist/*
```

---
  
## 📌 실행 파일(EXE) 생성 방법
  
### 🎯 Pyinstaller 설치
  
```bash
pip install pyinstaller
```
  
### 🎯 실행 파일 생성
  
```bash
pyinstaller --onefile your_script.py
```

옵션:
- `--onefile`: 단일 파일로 실행파일 생성
- `--windowed`: GUI 프로그램일 때 콘솔창 숨기기

---
  
## 📌 배포 시 주의사항
- 의존 패키지를 명시적으로 관리 (`requirements.txt`)
  
```bash
pip freeze > requirements.txt
pip install -r requirements.txt
```

- 배포 시 테스트 환경과 운영 환경을 구분하여 관리 권장

---
  
## 📌 연결 문서