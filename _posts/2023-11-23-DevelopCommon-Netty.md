---
title : "Netty"
excerpt : "Netty"
toc : true
toc_sticky : true
toc_label : "Netty"
categories:
- DevelopCommon
tags:
- [DevelopCommon]
last_modified_at: 2023-11-23T08:00:00-10:00:00
---

# 날짜 : 2023-11-23 11:11

# 태그 : #DevelopCommon
---

# 내용

## 정의
> Netty란?
>비동기 이벤트 기반 네트워크 애플리케이션 프레임워크

## 구조
  
![image](../../assets/Images/NettyStructure.png)

### Application Layer
- 실제 비즈니스로직
- 받아오는 데이터를 암복호화, 메시지프레이밍 등

### Transport Layer
- 추상화된 Network protocol을 포함한 API 제공

###  Network Layer
- 세부정보를 확인하여 입출력 관리
- 연결이 잘 되었는지 확인

## 특징
- 비동기
- 이벤트 기반
- 고성능
- 추상화

## Event Loop

### 기본 구조
  
![image](../../assets/Images/NettyEventLoop.png)

### sync(동기)
  
![image](../../assets/Images/NettySyncModel.png)

### async(비동기)
  
![image](../../assets/Images/NettyAsyncModel.png)

## 주요 Classes

### BootStrap
- Netty로 작성한 네트워크 애플리케이션의 동작 방식과 환경을 설정하는 도우미 클래스
- 추상화가 잘 돼있어, 설정이 쉽다.

#### 설정 가능 항목
- 전송 계층 (소켓 모드 및 IO type)
- 이벤트 루프 (단일 스레드, 다중 스레드)
- 채널 파이프라인 설정
- 소켓 주소와 포트
- 소켓 옵션

```java
.channel(NioSocketChannel.class)
.option(ChannelOption.TCP_NODELAY, true) //클라이언트 소켓 입출력 모드를 NIO로 설정
.option(ChannelOption.SO_KEEPALIVE, true) //클라이언트 소켓 모드를 KEEPALIVE로 설정

bootstrap.remoteAddress(tcpIp, tcpPort);
bootstrap.connect().addListener(new ConnectionListener(this)); 
```

### ServerBootStrap
- BootStrap 중에 서버의 설정을 돕기 위한 클래스
- Netty로 작성한 네트워크 애플리케이션이 시작할 때 가장 처음 수행되는 부분
- 수행할 동작과 환경을 설정

#### 설정 가능 항목
- 전송 계층 (소켓 모드 및 I/O 종류)
- 이벤트 루프 (단일스레드, 다중스레드)
- 서버 소켓 채널 이벤트 루프
- 소켓 채널 이벤트 루프
- 채널 파이프라인 설정
- 서버 소켓 채널 파이프라인 설정
- 소켓 주소와 포트
- 소켓 옵션

```java
.channel(NioServerSocketChannel.class) //서버 소켓 입출력 모드를 NIO로 설정
.handler(new LoggingHandler(LogLevel.INFO)) //서버 소켓 채널 핸들러 등록

ChannelFuture channelFuture = sb.bind(tcpPort).sync();
channelFuture.channel().closeFuture().sync();
```

### Event Loop Group
- Event Loop를 Grouping
- 주로 NioEventLoopGroup을 사용

```java
// 클라이언트 -> 서버 설정
Bootstrap bootstrap = new Bootstrap();
EventLoopGroup eventLoop = new NioEventLoopGroup();
bootstrap.group(eventLoop)

// 서버 -> 클라이언트 설정
ServerBootstrap sb = new ServerBootstrap();

// 클라이언트 연결을 수락하는 부모 스레드 그룹
EventLoopGroup bossGroup = new NioEventLoopGroup(bossCount);

// 연결된 클라이언트의 소켓으로 부터 데이터 입출력 및 이벤트를 담당하는 자식 스레드
EventLoopGroup workerGroup = new NioEventLoopGroup();

sb.group(bossGroup, workerGroup)
```

### ByteBuf
- Netty의 버퍼 클래스
- java.io.ByteBuffer와 유사하지만 더 나은 성능과 편의성

```java
// channelRead() 함수에서 데이터를 읽고/쓸때 사용
ByteBuf byteBuf = (ByteBuf) msg;
byte[] btLength = new byte[4];
byte[] bytes;
int length = byteBuf.readableBytes();

if (byteBuf.hasArray()) {
	bytes = byteBuf.array();
}

if (length >= 4) {
	// 최종적으로 btLength 배열에 bytes배열의 0부터 btLength 길이의 값을 복사
	System.arraycopy(bytes, 0, btLength, 0, 4);
}
```

### Future
- 작업이 완료되었다면 이를 애플리케이션에 알리는 한 방법
- 비동기 작업의 결과를 담는 자리 표시자
- 미래의 어떤 시점에 작업이 완료되면 그 결과를 접근 가능

### Channel
- 하나 이상의 입출력 작업(읽기 또는 쓰기)를 수행할 수 있는 하드웨어 장치, 파일, 네트워크 소켓, 프로그램 컴포넌트와 같은 엔티티에 대한 열린 연결
- 일반적인 소켓 프로그래밍에서 소켓과 동일한 의미

### **Channel Pipeline**
- Netty Channel과 이벤트 핸들러 사이의 연결 통로
- 채널에서 발생한 이벤트가 채널 파이프라인을 타고 흘러가고 이벤트 핸들러는 이벤트를 수신한 후에 본인이 처리할 이벤트인지 판단하고 처리
- 소켓채널로 수신된 데이터를 처리할 데이터핸들러를 지정

```java
		//Bootstrap
public static final SendHandler sendHandler = new SendHandler();

.handler(new ChannelInitializer<SocketChannel>() {//송수신 되는 데이터 가공 핸들러
	@Override
	protected void initChannel(SocketChannel ch) throws Exception {
		ChannelPipeline pipeline = ch.pipeline();
		pipeline.addLast(new IntegerHeaderFrameDecoder());
		pipeline.addLast(new LoggingHandler(LogLevel.INFO));
		pipeline.addLast(sendHandler);
	}
});

//ServerBootstrap
private ReceiveHandler RECEIVE_HANDLER; // = new ReceiveHandler();

.childHandler(new ChannelInitializer<SocketChannel>() { //송수신 되는 데이터 가공 핸들러
	@Override
	protected void initChannel(SocketChannel ch) throws Exception {
		ChannelPipeline pipeline = ch.pipeline();
		pipeline.addLast(new IntegerHeaderFrameDecoder());
		pipeline.addLast(new LoggingHandler(LogLevel.INFO));
		pipeline.addLast(RECEIVE_HANDLER);
	}
});
```

### Event

#### Inbound Event
- 연결 상대방이 어떤 Action을 했을 때, 발생

##### 이벤트 목록

| 이벤트명            | 발생 시점                                                                                 |
| ------------------- | ----------------------------------------------------------------------------------------- |
| channelRegistered   | 채널이 이벤트 루프에 등록되었을 때                                                        |
| channelActive       | 채널이 생성되고 이벤트 루프에 등록 된 이후, API를 사용하여 입출력을 수행할 상태가 됐을 때 |
| channelRead         | 데이터가 수신될 때마다                                                                    |
| channelReadComplete | 데이터 수신이 완료됐을 때마다                                                             |
| channelInactive     | 채널이 비활성화 됐을때                                                                    |
| channelUnregistered | 채널이 이벤트 루프에서 제거 됐을 때                                                       |

#### Oubound Event
- 프로그래머가 요청한 동작에 해당하는 이벤트

##### 이벤트 목록

| 이벤트명   | 발생 시점                                                              |
| ---------- | ---------------------------------------------------------------------- |
| bind       | 서버 소켓 채널에 클라이언트 연결을 대기하는 IP 포트가 설정 됐을때 발생 |
| connnect   | 클라이언트 소켓 채널이 서버에 연결되었을 때 발생                       |
| disconnect | 클라ㅓ이언트 소켓 채널의 연결이 끊어졌을 때 발생                       |
| close      | 소켓 채널의 연결이 닫혔을때 발생                                       |
| wirte      | 소켓 채널에 데이터가 기록되었을 때 발생                                |
| flush      | 소켓 채널에 flush 메서드가 호출되었을 때 발생                          |

#### Event Loop
- 이벤트가 올 때까지 대기하는 쓰레드
- NioEventLoop는 단일 쓰레드 이벤트 루프 (하나의 이벤트 루프에 하나의 쓰레드 할당)

### ChannelHandlerContext
- 채널에 대한 입출력 처리 및 채널 파이프라인에 대한 상호작용을 도와주는 인터페이스
- writeAndFlush() 메서드로 채널에 데이터를 기록
- writeAndFlush() 기록시, 바이트버퍼 형태로 변환
- close() 메서드로 채널 연결을 종료

## pipeline process
  
![image](../../assets/Images/NettyProcess.png)

### 1. 채널을 통해 메시지 전송

```java
Channel channel = ...
channel.writeAndFlush(message); 
```

### 2. Channel -> Channel pipeline으로 전송
- ChannelPipeline은 기본적으로 TailContext 와 HeaderContext를 가진다
- Tail과 Head 사이에 사용자가 등록한 ChannelHandlerContext가 Chane구조로 연결, 전달된 메시지가 체인을 따라 Outbound 방향으로 흐름

```java
public abstract class AbstractChannel ... {
    public ChannelFuture writeAndFlush(Object msg) {
        return pipeline.writeAndFlush(msg);
    }
}

public class DefaultChannelPipeline ... {
    public final ChannelFuture writeAndFlush(Object msg) {
        return tail.writeAndFlush(msg);
    }
}
```

### 3. 각각의 Handler 처리
- Handler에 바인딩 된 EventExecutor 쓰레드와 현재 메시지 전송을 요청하고 있는 쓰레드가 동일한지 체크
- 다른 쓰레드라면 메시지를 Queue에 삽입하고 그대로 실행 반환
- Queue에 쌓인 메시지는 이후에 EventExecutor에 의해 비동기적으로 처리
- Pipe라인의 첫 ChannelHandlerContext에서는 항상 메시지 Queue에만 쌓고 실행 반환

```java
abstract class AbstractChannelHandlerContext ... {
    private void write(Object msg, boolean flush, ChannelPromise promise) {
    	...
        EventExecutor executor = next.executor();
        if (executor.inEventLoop()) {
            if (flush) {
                next.invokeWriteAndFlush(m, promise);
            } else {
                next.invokeWrite(m, promise);
            }
        } else {
            final WriteTask task = WriteTask.newInstance(next, m, promise, flush);
            if (!safeExecute(executor, task, promise, m, !flush)) {
                task.cancel();
            }
        }
        ... 
    }
```

### 4. Executor
- 사용자가 별도 EventExecutor를 설정하지 않았다면 모든 Handler는 Channel의 EventLoop 쓰레드를 공유해서 사용
- Tail 외에는 Queue 메시지가 버퍼링 되는 일이 없다.
- EventExecutor가 있을 경우 Executor가 달라지는 Handler에서 Queue 메시지가 버퍼링 된 후 서로 다른 EventExecutor에 의해 메시지가 비동기적으로 처리

```java
abstract class AbstractChannelHandlerContext ... {
    public EventExecutor executor() {
        if (executor == null) {
            return channel().eventLoop();
        } else {
            return executor;
        }
    }
}
```

### 5. Pipeline을 통한 메시지는 다시 Channel로 전송

### 6. Netty Channel은 내부적으로 NIO 채널을 통해 네트워크로 메시지를 전송

```java
public class NioSocketChannel ... {
    protected void doWrite(ChannelOutboundBuffer in) throws Exception {
        SocketChannel ch = javaChannel();
        ... 
        ByteBuffer buffer = nioBuffers[0];
        int attemptedBytes = buffer.remaining();
        final int localWrittenBytes = ch.write(buffer);
        if (localWrittenBytes <= 0) {
            incompleteWrite(true);
            return;
        }
        ...
    }
}
```

---

# 연결문서
- [Socket](../../통신/통신-Socket)
- 
- [NIO](../../java/java-NIO)