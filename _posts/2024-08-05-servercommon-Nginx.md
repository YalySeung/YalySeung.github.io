---
title : "Nginx"
excerpt : "Nginx"
toc : true
toc_sticky : true
toc_label : "Nginx"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-08-05T08:00:00-10:00:00
---
  
---
  
 이 글에서는 Nginex 가 무엇인지 알아보고 설치부터 사용법까지 알아보겠다.

> **Nginx 란?**  
>
> 오픈 소스 웹 서버이자 리버스 프록시 서버, 로드 밸런서, HTTP 캐시 역할을 하는 소프트웨어이다. 
{: .notice--info}  
  
## Nginx의 역할
 Nginx를 사용하는 주 목적은 **정적 파일(HTML, CSS, JavaScript)을 서빙** 하는 것이다. 때문에 이에 최적화 되어있으며, **높은 성능**과 **적은 메모리 사용**으로 유명하다. 부가적으로 클라이언트 요청을 다른 AP서버로 전달하는 **리버스 프록시 서버**의 역할 및 요청을 분산해주는 **로드밸런서**의 역할도 할 수 있으며, **정적 데이터 캐싱** 및 인증서를 사용한 **보안 기능**도 지원한다.
  
## Nginx 설치
 필자는 Ubuntu 22.04.4 버전을 기준으로 설치 방법과 사용법 설명을 진행하겠다. 

 먼저 apt 업데이트 및 Nginx 설치를 진행한다.
  
```bash
sudo apt update
sudo apt install nginx
```

 **일부 라이브러리 다운로드가 안 될 경우** dns 설정과 저장소 url을 변경한다.
  
```bash
vi /etc/resolv.conf
```

 위 파일에 dns를 추가한다.

```
nameserver 8.8.8.8 
nameserver 8.8.4.4
```
  
```bash
vi /etc/apt/sources.list
```

 위 파일의 저장소 url을 변경한다.

```
deb http://archive.ubuntu.com/ubuntu/ jammy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ jammy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu jammy-security main restricted universe multiverse
```

 변경 후 다시 apt 업데이트 및 Nginx 설치를 진행한다.
  
```bash
sudo apt update
sudo apt install nginx
```
  
## 방화벽 설정
 설치가 완료 되었다면, 방화벽 설정을 진행한다.

 먼저 Nginx 에서 사용 가능한 방화벽 포트 정보를 조회한다.
  
```bash
sudo ufw app list
```
  
| Available App | port    |
| ------------- | ------- |
| Nginx Full    | 80, 443 |
| Nginx HTTP    | 80      |
| Nginx HTTPS   | 443     |

 필자는 http 접근만 허용할 예정이기 때문에 HTTP 포트를 허용하도록 설정하겠다.
  
```bash
sudo ufw allow 'Nginx HTTP'
```

 설정이 잘 됐는지 확인한다.
  
```bash
sudo ufw status
```

 만약 방화벽에 inactive 상태라면 활성화한다.
  
```bash
sudo ufw enable
```

 끝으로 Nginx 서비스가 활성화 되었는지 확인한다.
  
```bash
systemctl status nginx
```
  
## Nginx 프로세스 관리 명령어
 Nginx 프로세스를 관리할 수 있는 Command 목록이다.

| Command                      | 기능      |
| ---------------------------- | ------- |
| sudo systemctl start nginx   | 시작      |
| sudo systemctl stop nginx    | 종료      |
| sudo systemctl restart nginx | 재시작     |
| sudo systemctl reload nginx  | 리로드     |
| sudo systemctl disable nginx | 자동실행 방지 |
| sudo systemctl enable nginx  | 자동실행 설정 |
  
## 서버 블록 설정
 Nginx 설정은 모두 끝났으니, 웹 서비스를 서빙 할 수 있도록 설정을 진행하겠다. 먼저 서비스 할 정적 데이터를 준비한다. 필자는 React WebApp 을 준비했다.
  
![image](../../assets/images/React_Publish.png)

 아래 명령어를 순차적으로 수행한다.
  
```bash
  
# ex) 도메인 이름 : test.com
  
# 1. 디렉토리 생성:
sudo mkdir -p /var/www/<도메인 이름>/html 
{: .notice}  
  
# 2. 소유자 설정:
sudo chown -R $USER:$USER /var/www/<도메인 이름>/html 
{: .notice}  
  
# 3. 권한 설정:
sudo chmod -R 755 /var/www/<도메인 이름> 
{: .notice}  
  
# 4. 정적 데이터를 아래 경로로 이동:
  
# /var/www/도메인 이름/html/
  
# 5. 서버 블록 생성:
sudo vi /etc/nginx/sites-available/<도메인 이름> 
{: .notice}  
  
# 아래 내용 입력:
server {
    listen 80;
    listen [::]:80;

    root /var/www/<도메인 이름>/html; 
{: .notice}  
    index index.html index.htm index.nginx-debian.html;

    server_name <도메인 이름> www.<도메인 이름>; 
{: .notice}  

    location / {
        try_files $uri $uri/ =404;
    }
}
  
# 6. 심볼릭 링크 생성:
sudo ln -s /etc/nginx/sites-available/<도메인 이름> /etc/nginx/sites-enabled/ 
{: .notice}  
  
# 7. nginx.conf 파일 설정:
sudo vi /etc/nginx/etc/nginx
  
# 아래 내용으로 수정:
...
http {
    ...
    server_names_hash_bucket_size 64;
    ...
}
...
  
# 8. 설정 파일에 문법 오류가 없는지 검사:
sudo nginx -t
  
# 9. Nginx 재시작:
sudo systemctl restart nginx
```

 만약 localhost:80으로 접속 했을 때,  nginx welcome 페이지가 보인다면 symlink가 /etc/nginx/sites-enabled/default 경로를 바라보고 있을 가능성이 크다. 따라서 symlink에서 default 를 제거한다.
  
```bash
rm /etc/nginx/sites-enabled/default
  
# Nginx 재시작:
sudo systemctl restart nginx
```

 다시 localhost:80으로 접속하여 결과를 확인하자!

---
  
# 연결문서
- [VirtualBox-Ubuntu](../../developcommon/developcommon-VirtualBox-Ubuntu)
- [Ubuntu-MariaDB설치-Online](../../os/os-Ubuntu-MariaDB설치-Online)