---
title : "Linux Command Detail"
excerpt : "Linux Command Detail"
toc : true
toc_sticky : true
toc_label : "Linux Command Detail"
categories:
- CLI
tags:
- [CLI, Linux]
last_modified_at: 2023-11-08T08:00:00-10:00:00
---
  
---
  
## 명령어
  
### jmap
  
#### JVM heap 메모리 사용량 확인
  
```bash
jmap -heap <pid>
```
  
#### heap 덤프 파일 생성
  
```bash
jmap -dump:live,file=<덤프파일경로> <프로세스ID>
```  
- dump:live : 현재 heap 내의 액티브 메모리 레퍼런스가 있는 object만 캡처
  
### top
  
```bash
top
```
  
![image](../../assets/images/LinuxTopResult.png)
  
#### Summary Region
- 전체 프로세스가 OS에 대해서 리소스를 어느정도 차지하는지 표시
- system time, up time, user
- Load Average
- Task
- CPU
- Memory
  
#### Detail Region
- 각 Task 별 상세내역 표시
  
##### PID
- 프로세스 ID
  
##### USER
- 해당 프로세스를 실행한 User 또는 효과를 받는 User
  
##### PR & NI
- PR : 커널에 의해서 스케쥴링 되는 우선순위
- NI : PR에 영향을 주는 nice 값
  
##### VRIT
- 프로세스가 소비하고 있는 총 메모리
- 프로그램이 실행중인 코드, heap, stack과 같은 메모리, IO buffer 메모리를 포함
  
##### RES
- RAM에서 사용중인 메모리의 크기
  
##### SHR
- 다른 프로세스와의 공유메로리를 나타냅니다.
  
##### %MEM
- RAM에서 RES가 차지하는 비율
  
##### S
- 프로세스의 현재 상태
  
##### TIME+
- 프로세스가 사용한 토탈 CPU 시간
  
##### COMMAND
- 해당 프로세스가 실행한 커맨드
  
#### 보고싶은 순으로 정렬
- shift + m : 메모리 사용량 순으로 정렬
- shift + p : CPU 사용량 순으로 정렬
- shift + n : process id 로 정렬
- shift + t : running time 순으로 정렬
- shift R : 오름차순과 내림차순을 토글 변경
  
### shutdown
- 서버 종료 후 **재부팅**
  
#### 종료
  
```bash
shutdown -h now 
```
  
### chmod
  
#### 파일 실행 권한 부여
  
```bash
// 현재 폴더 경로의 모든 shell 파일 실행 권한 부여
chmod +x *.sh
```
  
### ln
  
#### Symbolic link 생성
  
```bash
ln -s <대상파일> <link 명>
```
  
### alias
  
#### 현재 등록된 사용자 별칭 확인
  
```bash
alias
```
  
#### 별칭 등록
  
```bash
alias <별칭>='<명령어>'
```
  
#### 별칭 해제
  
```bash
unalias <별칭>
```
  
## ip 확인
  
```bash
ifconfig
```
 장치명과 ip주소를 확인 할 수 있다.
  
## 계정
  
### adduser
  
```bash
adduser <계정명>
```
  
### useradd
  
```bash
useradd <계정명>
passwd <비밀번호>
groupadd <그룹명>
usermod -G <그룹명> <계정명>
usermod -s /bin/bash <계정명>
grep /bin/bash /etc/passwd | cut -f1 -d:
```
  
### userdel
  
```bash
userdel <계정명>
```

---
  
# 연결문서
- [CLI](../../cli/cli-CLI)
- [CLI-BaseCommand](../../cli/cli-CLI-BaseCommand)