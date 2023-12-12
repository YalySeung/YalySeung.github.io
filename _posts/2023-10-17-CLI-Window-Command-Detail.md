---
title : "Window-Command-Detail"
excerpt : "Window-Command-Detail"
toc : true
toc_sticky : true
toc_label : "Window-Command-Detail"
categories:
- CLI
tags:
- [CLI]
last_modified_at: 2023-10-17T08:00:00-10:00:00
---

# 날짜 : 2023-10-17 10:07

# 태그 : #CLI
---

# 내용

## 명령어

### netstat
- 컴퓨터에 연결된 모든 네트워크 정보를 보여줌

#### 옵션
- -a : 모든 포트 표시
- -n : <IP주소>:<포트> 형식으로 보여줌
-  -o :  프로세스 ID를 표시

#### 포트의 상태
- LISTENING : 통신을 하기를 대기하고 있는 상태입니다. (아직 통신중이 아님)
- CLOSE-WAIT : 연결이 종료되기를 대기하고 있는 상태입니다.
- CLOSED : 연결이 종료된 상태
- TIME-WAIT : 연결 종료 후 일정시간 유지하고 있는 상태(일정 시간 이후 완전 종료)
- ESTABLISHED : TCP에서 3 Way Handshake 이후 통신중인 상태
- SYS-SENT : 통신 상태에게 SYN 패킷을 보낸 후 연결을 요청한 상태
- 공백 : 상태값이 없는 경우는 UDP 프로토콜을 사용하는 경우

#### 예시

```bash
netstat -ano | find "LISTEN"
```
  
![image](./../../assets/images/FindListenPort.png)

```bash
netstat -anp tcp | find "LISTEN"
```
  
![image](./../../assets/images/FindListenTCPPort.png)

```bash
netstat -anp tcp | find "443"
```
  
![image](./../../assets/images/Find443Port.png)

```bash
netstat -anp tcp | findstr 49414
```
  
![image](./../../assets/images/FindSpecificPort.png)

### tasklist
- 실행중인 process list를 보여줌
- 리눅스의 ps와 같은 명령어

#### 옵션
- /SVC : 각 프로세스에 호스트된 서비스
- /V : 자세한 작업정보
- /M : 각 프로세스와 관련된 모듈 나열

#### 예시

```bash
tasklist
```
  
![image](./../../assets/images/../../assets/Images/Tasklist.png)

```bash
tasklist /M | findstr "RuntimeBroker"
```
  
![image](./../../assets/images/../../assets/Images/TaskListRuntimeBroker.png)

```bash
tasklist /V
```
  
![image](./../../assets/images/../../assets/Images/TaskListDetails.png)

### sc
- 서비스 관련 CLI

#### sc delete \<서비스명\>
- **관리자 콘솔로만 사용 가능**

---

# 연결문서
