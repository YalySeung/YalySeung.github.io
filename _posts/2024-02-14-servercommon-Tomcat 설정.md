---
title : "Tomcat 설정"
excerpt : "Tomcat 설정"
toc : true
toc_sticky : true
toc_label : "Tomcat 설정"
categories:
- ServerCommon
tags:
- [ServerCommon]
last_modified_at: 2024-02-14T08:00:00-10:00:00
---
  
---
  
## 톰캣 설정파일
  
![image](../../assets/images/Tomcat_Conf.png)
  
## server.xml
- 메인 설정 파일
- Service, Connector, Host 정보 설정
  
```xml

<?xml version="1.0" encoding="UTF-8"?> 
{: .notice}  
<Server port="8005" shutdown="SHUTDOWN"> 
{: .notice}  
<Listener className="org.apache.catalina.startup.VersionLoggerListener" /> 
{: .notice}  
<Listener className="org.apache.catalina.core.AprLifecycleListener" SSLEngine="on" /> 
{: .notice}  
<Listener className="org.apache.catalina.core.JreMemoryLeakPreventionListener" /> 
{: .notice}  
<Listener className="org.apache.catalina.mbeans.GlobalResourcesLifecycleListener" /> 
{: .notice}  
<Listener className="org.apache.catalina.core.ThreadLocalLeakPreventionListener" /> 
{: .notice}  

<GlobalNamingResources> 
{: .notice}  
  <Resource name="UserDatabase" auth="Container"
			type="org.apache.catalina.UserDatabase"
			description="User database that can be updated and saved"
			factory="org.apache.catalina.users.MemoryUserDatabaseFactory"
			pathname="conf/tomcat-users.xml" /> 
{: .notice}  
  <Resource name="jdbc/MyDB"
	global="jdbc/MyDB"
	auth="Container"
	type="javax.sql.DataSource"
	driverClassName="com.mysql.jdbc.Driver"
	url="jdbc:mysql://localhost:3306/UserDB"
	username="user1"
	password="pass1"        
	maxActive="100"
	maxIdle="20"
	minIdle="5"
	maxWait="10000"
	validationQuery="select 1 from dual"
	/> 
{: .notice}  
</GlobalNamingResources> 
{: .notice}  

<Service name="Catalina"> 
{: .notice}  
  <Connector port="8080" protocol="HTTP/1.1"
			connectionTimeout="20000"
			redirectPort="8443" /> 
{: .notice}  
  <Engine name="Catalina" defaultHost="localhost"> 
{: .notice}  
	<Realm className="org.apache.catalina.realm.LockOutRealm"> 
{: .notice}  
	  <Realm className="org.apache.catalina.realm.UserDatabaseRealm"
			resourceName="UserDatabase"/> 
{: .notice}  
	</Realm> 
{: .notice}  
	<Host name="localhost"  appBase="webapps"
		  unpackWARs="true" autoDeploy="true"> 
{: .notice}  
	  <Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs"
			prefix="localhost_access_log" suffix=".txt"
			pattern="%h %l %u %t &quot;%r&quot; %s %b" /> 
{: .notice}  
	</Host> 
{: .notice}  
  </Engine> 
{: .notice}  
</Service> 
{: .notice}  
</Server> 
{: .notice}  

```
  - Server, Resoure, Connector, Host를 주의깊게 보도록 하자.\
  
## 컴포넌트 별 설명
- [Server](#server) : server.xml의 최상위 컴포넌트
- [Listener](#listener) : Listener 모듈 등록
- [GlobalNamingResources](#globalnamingresources) : global JNDI 리소스들을 정의
- [Resource](#resource): global JNDI 리소스
- [Service](#service): Connectors와 Engine 을 정의하는 프로퍼티
- [Connector](#connector): Listening Server 정보 설정, 2개 포트에서 요청을 처리하겠다면 2개도 등록 가능
- [Engine](#engine): DB Access 처리 라이브러리와 host 정보를 처리하는 컴포넌트
- [Realm](#realm): 사용자에 할당된 데이터베이스 관리 및 컨테이너 관리 보안 구현, 사용할 Realm 클래스들 명시
- [Host](#host): 가상의 Host를 정의
- [Value](#value): Catalina 컨테이너에 대한 요청 처리 파이프라인에 삽입될 구성요소
  
### Server
  
```xml
<Server port="8005" shutdown="SHUTDOWN"> 
{: .notice}  
  <Listener .../> 
{: .notice}  
  ...

  <GlobalNamingResources> 
{: .notice}  
	...
  </GlobalNamingResources> 
{: .notice}  

  <Service> 
{: .notice}  
	...
  </Service> 
{: .notice}  
</Server> 
{: .notice}  
```  
- <span style="color:#82aaff">port</span> : TCP/IP port 
{: .notice}  
- <span style="color:#82aaff">shutdown</span> : Tomcat 종료를 위한 Command String 
{: .notice}  
  
### Listener
  
```xml
<Listener className="org.apache.catalina.startup.VersionLoggerListener" /> 
{: .notice}  
<Listener className="org.apache.catalina.core.AprLifecycleListener" SSLEngine="on" /> 
{: .notice}  
<Listener className="org.apache.catalina.core.JreMemoryLeakPreventionListener" /> 
{: .notice}  
<Listener className="org.apache.catalina.mbeans.GlobalResourcesLifecycleListener" /> 
{: .notice}  
<Listener className="org.apache.catalina.core.ThreadLocalLeakPreventionListener" /> 
{: .notice}  
```  
- <span style="color:#c3e88d">VersionLoggerListener</span> : Tomcat 기동시, 버전 정보를 기록하는 Listener, Server컴포넌트의 첫줄에 위치해야한다. 
{: .notice}  
- <span style="color:#c3e88d">AprLifecycleListener</span> : APR을 초기화, 파괴하는 Listener 
{: .notice}  
- <span style="color:#c3e88d">JreMemoryLeakPreventionListener</span> : Java 런타임 환경의 메모리 누수, 파일lock 등에 대한 해결방법 제공 Listener 
{: .notice}  
- <span style="color:#c3e88d">GlobalResourcesLifecycleListener</span> : JNDI 자원과 연관된 MBean들을 인스턴스화하는 Listener 
{: .notice}  
- <span style="color:#c3e88d">ThreadLocalLeakPreventionListener</span> : 메모리 누구로 컨텍스트가 중지될 때, Executor 풀에서 스레드 갱신을 트리거하는 Listener 
{: .notice}  
  
### GlobalNamingResources
  
```xml  
<GlobalNamingResources> 
{: .notice}  
  <Resource name="jdbc/MyDB"
	global="jdbc/MyDB"
	.../> 
{: .notice}  
</GlobalNamingResources> 
{: .notice}  
```  
- <span style="color:#89ddff">Resource</span> : Tomcat/lib 경로에 dbms에 맞는 jdbc 드라이버가 존재할 경우, 위와같이 DB정보를 명시하여 web.xml 또는 context.xml 에서 불러올 수 있다. 
{: .notice}  
  
```xml
//web.xml
<resource-ref> 
{: .notice}  
  <description>Employees Database for HR Applications</description> 
{: .notice}  
  <res-ref-name>jdbc/EmployeeDB</res-ref-name> 
{: .notice}  
  <res-ref-type>javax.sql.DataSource</res-ref-type> 
{: .notice}  
  <res-auth>Container</res-auth> 
{: .notice}  
</resource-ref>\ 
{: .notice}  
```
  
### Resource
  
```xml
<Resource name="jdbc/MyDB"
  global="jdbc/MyDB"
  auth="Container"
  type="javax.sql.DataSource"
  driverClassName="com.mysql.jdbc.Driver"
  url="jdbc:mysql://localhost:3306/UserDB"
  username="user1"
  password="pass1"        
  maxActive="100"
  maxIdle="20"
  minIdle="5"
  maxWait="10000"
  validationQuery="select 1 from dual"
  /> 
{: .notice}  
```  
- <span style="color:#89ddff">Resource</span> : Tomcat/lib 경로에 dbms에 맞는 jdbc 드라이버가 존재할 경우, 위와같이 DB정보를 명시하여 web.xml 또는 context.xml 에서 불러올 수 있다. 
{: .notice}  
- <span style="color:#82aaff">auth</span> : Application or Container 값을 갖는다. 
{: .notice}  
- <span style="color:#82aaff">name</span> : 리소스를 불러올 때 사용할 식별자 
{: .notice}  
- <span style="color:#82aaff">type</span> : 리소스 종류 
{: .notice}  
- <span style="color:#82aaff">description</span> : 리소스에 대한 설명 
{: .notice}  
- <span style="color:#82aaff">url, username, password, maxActive, maxIdle, minIdle, maxWait</span> : DB 관련 정보   
{: .notice}  
- <span style="color:#82aaff">validationQuery </span>: DB 테스트 sql  
{: .notice}  
  
### Service
  
```xml
<Service name="Catalina"> 
{: .notice}  
  <Connector> 
{: .notice}  
  ...
  </Connector> 
{: .notice}  
  <Engine> 
{: .notice}  
  ...
  </Engine> 
{: .notice}  
</Service> 
{: .notice}  
```  
- <span style="color:#82aaff">name</span> : 기본값은 Catalina, HTTP/AJP 엔진 선택자 
{: .notice}  
  
### Connector
  
```xml
<Connector port="8080" protocol="HTTP/1.1"
		   connectionTimeout="20000"
		   redirectPort="8443" /> 
{: .notice}  
```  
- <span style="color:#82aaff">port</span> : TCP 수신 포트 
{: .notice}  
- <span style="color:#82aaff">protocol</span> : 통신 프로토콜 
{: .notice}  
- <span style="color:#82aaff">connectionTimeout</span> : Connnector timeout millsec 
{: .notice}  
- <span style="color:#82aaff">redirectPort</span> : ssl 요청에 대한 re-direct 포트   
{: .notice}  
  
### Engine
  
```xml
<Engine name="Catalina" defaultHost="localhost"> 
{: .notice}  
  <Realm className="org.apache.catalina.realm.LockOutRealm"> 
{: .notice}  
	<Realm className="org.apache.catalina.realm.UserDatabaseRealm"
		   resourceName="UserDatabase"/> 
{: .notice}  
  </Realm> 
{: .notice}  
  <Host name="localhost"  appBase="webapps"
		unpackWARs="true" autoDeploy="true"> 
{: .notice}  
	<Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs"
		   prefix="localhost_access_log" suffix=".txt"
		   pattern="%h %l %u %t &quot;%r&quot; %s %b" /> 
{: .notice}  
  </Host> 
{: .notice}  
</Engine> 
{: .notice}  
```  
- <span style="color:#82aaff">name</span> : 로깅시 표기될 Engine 의 고유한 논리명 
{: .notice}  
- <span style="color:#82aaff">defaultHost</span> : 기본 Host명, Host컴포넌트의 name과 일치해야한다. 
{: .notice}  
  
### Realm
  
```xml
<Realm className="org.apache.catalina.realm.LockOutRealm"> 
{: .notice}  
  <Realm className="org.apache.catalina.realm.UserDatabaseRealm"
		 resourceName="UserDatabase"/> 
{: .notice}  
</Realm> 
{: .notice}  
```  
- <span style="color:#82aaff">className</span> : 사용할 Realm 클래스명 
{: .notice}  
- <span style="color:#82aaff">resourceName</span> : 사용할 Resource 명 
{: .notice}  
  
### Host
  
```xml
<Host name="localhost"  appBase="webapps"
	  unpackWARs="true" autoDeploy="true"> 
{: .notice}  
  <Valve .../> 
{: .notice}  
</Host> 
{: .notice}  
```  
- <span style="color:#82aaff">name</span> : host명 
{: .notice}  
- <span style="color:#82aaff">appBase</span> : webapps 경로 
{: .notice}  
- <span style="color:#82aaff">unpackWARs</span> : WAR 파일을 압축해제할 것인지 
{: .notice}  
- <span style="color:#82aaff">autoDeploy</span> : Tomcat이 실행중인동안 주기적으로 웹 프로그램 업데이트 내용 확인할지 여부, appBase 경로의 업데이트 내역을 확인한다.   
{: .notice}  
  
### Value
  
```xml
<Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs"
	   prefix="localhost_access_log" suffix=".txt"
	   pattern="%h %l %u %t &quot;%r&quot; %s %b" /> 
{: .notice}  
```  
- <span style="color:#82aaff">className</span> : 사용할 java 클래스명 
{: .notice}  
- <span style="color:#82aaff">directory</span> : 로그파일이 생성될 디렉토리 경로 
{: .notice}  
- <span style="color:#82aaff">prefix</span> : 로그파일 prefix 
{: .notice}  
- <span style="color:#82aaff">suffix</span> : 로그파일 suffix 
{: .notice}  
- <span style="color:#82aaff">pattern</span> : 로그 내용의 시간 표기 패턴 
{: .notice}  

---
  
# 연결문서
- [Tomcat](../../servercommon/servercommon-Tomcat)
- [Tomcat-logging](../../servercommon/servercommon-Tomcat-logging)