---
title : "Ubuntu MariaDB설치 Online"
excerpt : "Ubuntu MariaDB설치 Online"
toc : true
toc_sticky : true
toc_label : "Ubuntu MariaDB설치 Online"
categories:
- OS
tags:
- [OS]
last_modified_at: 2024-07-23T08:00:00-10:00:00
---
  
---
  
 이 글에서는 **Ubuntu OS**에 **Mariadb**를 설치하는 방법에 대해서 알아보겠다.
  
## 1. 패키지 업데이트
  
```bash
// 시스템 패키지 목록 업데이트
sudo apt update

// 설치된 모든 패키지를 최신 버전으로 업데이트
sudo apt upgrade -y

// software-properties-common : 추가 소스나 Personal Package Archives 관리도구
// dirmngr : GPG 키 관리 도구, 서명된 패키지의 검증 지원
// ca-certificates : 인증 기관의 인증서 패키지, https 지원
// apt-transport-https : API의 HTTPS를 사용한 패키지를 다운로드 지원
sudo apt-get install curl software-properties-common dirmngr ca-certificates apt-transport-https -y 

// MariaDB 저장소 설정 스크립트 다운로드
sudo curl -LsS https://downloads.mariadb.com/MariaDB/mariadb_repo_setup 

// MariaDB 저장소 설정 스크립트를 실행하여 10.5 버전 저장소 설정
sudo bash -s -- --mariadb-server-version=10.5 apt update
```
  
## MariaDB 설치
 설치 준비가 완료되었으니 설치를 진행하자. 보안 설정은 독자의 판단에 따라 진행한다.
  
```bash
// 패키지 설치
sudo apt install mariadb-server mariadb-client mariadb-backup

// 보안 설정
sudo mysql_secure_installation
```
  
## 외부 접속 설정
  
### Mariadb 설정
 먼저 mariadb 설정파일에서 **port**와 **bind-address**를 설정한다. 필자는 /etc/mysql/mariadb.conf.d/50-server.cnf 파일을 수정했다. 

```
[mysqld]
bind-address = 0.0.0.0
port = 3309
...
```

 상황에 따라 설정파일이 여러개 존재할 수 있다. 이럴때는 내가 원하는 속성을 가진 설정파일을 찾아 수정하는 편이 좋다. grep 커맨드로 폴더 하위의 모든 파일을 대상으로 내가 원하는 text를 검색한다.
  
``` bash
sudo grep -r 'bind_address' /etc/mysql/
```

 설정이 모두 완료되었다면 mariadb를 실행한다.
  
```bash
systemctl start mariadb
```

 내가 설정한 설정한 포트 정보와 외부 접속 정보가 적용되었는지 확인한다.
  
```bash
sudo netstat -tulnp | grep 3309
```
  
![image](../../assets/images/MariaDBServiceResult.png)

 접속 가능한 사용자 정보가 **0.0.0.0:\<mariadbPort\>** 일 경우에 외부에서 접속이 가능하다.

> **caution**
>
> Mariadb 서비스가 실행 중 일 때,  설정값 수정이 필요하면 꼭 재기동을 해주어야 한다. 
{: .notice--danger}  
  
```bash
// 서비스 재기동
systemctl restart mariadb
```

 MariaDB는 다른 DB와 다르게 **외부에서 접속할 수 있는 사용자 정보를 DB제공**해야 한다. MariaDB에 접속하여 권한을 추가하자.
  
```bash
// DB 접속
mysql -u root
```
  
```sql
// 사용자 접속 권한 부여
`GRANT ALL PRIVILEGES ON mydatabase.* TO <사용자명>@<ip> IDENTIFIED BY <비밀번호>; FLUSH PRIVILEGES;`
```

 ip를 **%**로 설정할 경우 사용자 명만 체크한다.
  
### 방화벽 설정
 MariaDB 설정은 끝났지만 아직 방화벽 설정이 남아있다. 먼저 현재 방화벽 설정을 조회하자. 필자는 **ufw(Uncomlicated Firewall)**를 사용하겠다.
  
```bash
// 방화벽 정보 조회
sudo ufw status
```

 ufw 유틸리티를 사용할 수 없다면, 사용 가능한 상태로 변경한다.
  
```bash
sudo ufw enable
```

 여기에 mariadb 포트가 추가되어 있지 않다면 추가한다.
  
```bash
sudo ufw allow 3309/tcp
```

 MariaDB 설치 완료!

---
  
# 연결문서
- [Linux-방화벽및포트](../../os/os-Linux-방화벽및포트)
- [Linux-MariaDB설치-Offline](../../os/os-Linux-MariaDB설치-Offline)