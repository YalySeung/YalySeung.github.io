---
title : "python 프로젝트"
excerpt : "python 프로젝트"
toc : true
toc_sticky : true
toc_label : "python 프로젝트"
categories:
- python
tags:
- [미완료]
last_modified_at: 2023-11-27T08:00:00-10:00:00
---

# 날짜 : 2023-11-27 12:19

# 태그 : #미완료 
---

# 내용

## 파이썬 설치

## 환경변수 설정

## vs 코드 확장 설치

## setuptools 설치

```bash
pip install setuptools
```

## 패키지 다운로드

```bash
python <셋업 파일명> install
```

## 빌드 및 패키지 시작

### source distribution 생성

```bash
python setup.py sdist
```

```bash
pip install dist/your_project_name-1.0.0.tar.gz
```

### 개발 모드로 시작

```bash
pip install -e .
```

### 공개 배포

```bash
pip install twine twine upload dist/
```

## exe 빌드

### pyinstaller 설치

```bash
pip install pyinstaller
```

### 실행파일 생성

```bash
pyinstaller <setup 스크립트>
```

---

# 연결문서
