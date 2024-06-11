---
title : "Linux ip변경"
excerpt : "Linux ip변경"
toc : true
toc_sticky : true
toc_label : "Linux ip변경"
categories:
- OS
tags:
- [Linux, OS]
last_modified_at: 2024-05-23T08:00:00-10:00:00
---
  
---
  
 이번 글에서는 리눅스 IP 변경 방법을 알아보도록 하겠다.

 리눅스에서 **네트워크 설정파일**은 **/etc/sysconfig/network-scripts** 경로에 존재한다. 이 경로에는 다양한 설정파일이 존재하는데 내가 수정할 설정파일을 찾기 위해 먼저 **장치명**과** ip주소**를 확인해야한다.
  
```bash
ifconfig
```
  
![image](../../assets/images/ifconfig%202.png)

 위와 같이 명령어를 입력하면 장치명과 ip주소를 확인할 수 있다. **설정파일 명**은 **ifcfg-<장치명>** 의 포맷이니 한번 열어보자. 
{: .notice}  
  
![image](../../assets/images/LinuxNetworkConfig.png)

 위 파일의 **IPADDR** 항목과 **GATEWAY**를 변경해준다. 파일만 변경한다고 IP 주소가 변경되지 않는다. **네트워크를 재시작 하여 설정파일이 반영**되도록 하자
  
```bash
sudo service network restart
```

 필자의 경우 재시작 후 바로 ip가 변경되었지만, 간혹 설정파일을 수정했던 장치가 인식되지 않는 경우가 있다. 이럴 경우에는 **장치를 활성화**하자
  
```bash
sudo ifup em1
```

 여기까지 완료했다면, 다시 ip 확인하는 명령어로 잘 적용 되었는지 확인해본다.

---
  
# 연결문서
