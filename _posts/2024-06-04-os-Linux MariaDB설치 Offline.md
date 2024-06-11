---
title : "Linux MariaDB설치 Offline"
excerpt : "Linux MariaDB설치 Offline"
toc : true
toc_sticky : true
toc_label : "Linux MariaDB설치 Offline"
categories:
- OS
tags:
- [Linux, MariaDB]
last_modified_at: 2024-06-04T08:00:00-10:00:00
---
  
---
  
 이 글에서는 **이더넷이 안되는 환경**의 Linux PC에 **MariaDB를 설치하는 방법**에 대해 이야기 해보겠다.

 먼저 MariaDB의 내부를 살펴보면 크게 DB데이터를 담는 **data영역**과 동작 관련된 라이브러리를 담고 있는 **binary 영역**으로 나뉘어 있음을 인지하고 설치를 진행하도록 하겠다.
   
![image](../../assets/images/MariaDBStructure.png)

 Offline 환경에서는 yum, apt-get 등을 사용할 수 없기 때문에 **외부 PC에서 바이너리 파일을 직접 다운로드 받아 대상 PC에 넣어야 한다**. [다운로드 링크]([https://downloads.mariadb.org/mariadb/](https://downloads.mariadb.org/mariadb/))에서 binary 파일을 다운로드 하자.
  
![image](../../assets/images/MariaDBBinaryDownload.png)
 
 필자는 10.6.18 버전에 64bit 바이너리 파일을 사용하도록 하겠다. 다운받은 바이너리 압축 파일을 설치할 PC로 이동시키고, **압축을 해제**한다. 필자는 **/home/mariadb**에 압축을 해제했다. 이 경로는 이후에 **MariaDB 설정 파일**과 **서비스 설정 파일**에 사용해야 하니 잘 기억해두도록 하자
  
```bash
//압축 해제
tar -zxvf mariadb*.tar.gz
```

 압축을 해제 했다면, Mariadb 설정파일을 추가하고 수정하도록 한다. 
  
```bash
vi /etc/my.cnf
```

 파일을 열어 아래 내용을 추가한다.
 
```
[mysqld] 
character-set-server=utf8mb4 //인코딩 설정
collation-server=utf8mb4_bin 
basedir=/home/mariadb //라이브러리 경로 설정
datadir=/home/data //data 경로 설정

[mysqld_safe] 
log-error=/var/lib/mysql/log/mariadb.log // 로그 경로 지정
pid-file=/home/mariadb.pid // 프로세스 id 파일 경로 지정
```

 준비가 완료되면 mariadb에서 제공하는 **script로 설치를 진행**한다. 주의해야 할 점은 **mariadb 탑 디렉토리에서 실행**해야 에러 없이 설치 된다. 여기서 **사용자는 관리자 계정명**을 의미한다.
  
```bash
cd /home/mariadb
.scripts/mysql_install_db
```

 PC 재기동시에도 MariaDB가 자동으로 실행 될 수 있도록 **서비스로 등록**해야 한다. 먼저 **service 설정파일을 열어 user와 group을 설정**해준다. 여기서 **user**는 **관리자 계정명**이고, **group**은 **linux 계정명**이다.
  
```bash
cd /home/mariadb/support-files/systemd 
vi mariadb.service 
  
# 이 부분을 앞서 생성했던 사용자와 그룹명으로 설정해야 함. 
USER= 
GROUP= 
```

> **caution**
>
> mariadb.service 파일 내 모든 경로는 내가 다운 받은 binary 파일의 bin 경로를 기준으로 설정해야 한다. 
{: .notice--danger}  

 파일 수정이 완료되었다면 mariadb.service 파일을 system 경로로 복사하여 **linux 서비스로 등록**한다.
  
```bash
cp mariadb.service /etc/systemd/system/
```

 서비스로 등록이 완료되면, **서비스를 시작하여 MariaDB가 실행되는지 확인**한다.
  
```bash
systemctl start mariadb.service​ //서비스 실행
systemctl status mariadb.service //서비스 상태 확인
```

 서비스를 실행했다면, mariadb 명령어 사용을 위해 **환경변수를 등록**해보자. **global 환경 변수는 /etc/profile를 수정하여 추가**할 수 있다.
  
```bash
vi /etc/profile
```

 파일을 열었다면, 아래 내용을 추가한다.
  
```bash
export MARIADB_HOME=/home/mariadb
export PATH=$PATH:$MARIADB_HOME/bin:.
```

 변경된 수정사항을 바로 적용하려면 **source 명령어**를 사용한다.
  
```bash
source /etc/profile
```

 MariaDB에 접속하여 root 계정의 **패스워드를 지정**한다.
  
```bash
mysql -uroot // 접속
  
# root 패스워드 설정 
msqladmin -uroot password '패스워드'
```

여기까지 따라왔다면, 이제 MariaDB를 마음껏 사용해보자!

---
  
# 연결문서
