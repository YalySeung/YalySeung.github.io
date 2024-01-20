---
title : "Reactor"
excerpt : "Reactor"
toc : true
toc_sticky : true
toc_label : "Reactor"
categories:
- DesignPattern
tags:
- [DesignPattern]
last_modified_at: 2023-11-23T08:00:00-10:00:00
---

# 날짜 : 2023-11-23 17:00

# 태그 : #DesignPattern
---

# 내용

## 정의
> **Reactor 패턴이란?**
>
> 동시에 들어오는 서비스 처리 요청을 관리하는 이벤트 처리 디자인 패턴
{: .notice--info}

## 특징
- 이벤트 처리를 비동기적으로 수행하며, 단일 스레드에서 이벤트를 효율적으로 처리할 수 있는 구조
- 순차처리
- 싱글 스레드

## Reactor의 리벤트 처리 프로세스
- 이벤트에 반응할 reactor생성, 이벤트를 처리할 event handler 등록
- reactor는 이벤트가 발생대기
- 이벤트가 수신되면 selector를 통해 handler에게 이벤트 전달

## 구조
  
![image](../../assets/images/ReactorStructure.png)

### Reactor
- 싱글스레드
- 이벤트를 전방에서 수신
- EventType 과 EventHandler를 맵핑하여 가지고 있음

```java
public class Reactor {  
    private int port = 80;  
    private final Selector selector;  
    private final ServerSocketChannel serverSocketChannel;  
    private final EventHandler eventHandler;  
  
    public Reactor(EventHandler eventHandler) throws IOException {  
        this.selector = Selector.open();  
        this.serverSocketChannel = ServerSocketChannel.open();  
        this.serverSocketChannel.socket().bind(new InetSocketAddress(port));  
        this.serverSocketChannel.configureBlocking(false);  
        this.serverSocketChannel.register(selector, SelectionKey.OP_ACCEPT);  
        this.eventHandler = eventHandler;  
    }  
  
    public void run() throws IOException {  
        while (true) {  
            selector.select();  
  
            Set<SelectionKey> selectedKeys = selector.selectedKeys();  
            Iterator<SelectionKey> keyIterator = selectedKeys.iterator();  
  
            while (keyIterator.hasNext()) {  
                SelectionKey key = keyIterator.next();  
                keyIterator.remove();  
  
                if (key.isAcceptable()) {  
                    handleAccept();  
                } else if (key.isReadable()) {  
                    handleRead(key);  
                }  
            }  
        }  
    }  
  
    private void handleAccept() throws IOException {  
        SocketChannel socketChannel = serverSocketChannel.accept();  
        socketChannel.configureBlocking(false);  
        socketChannel.register(selector, SelectionKey.OP_READ);  
  
        Event event = new Event(socketChannel);  
        eventHandler.handleEvent(event);  
    }  
  
    private void handleRead(SelectionKey key) throws IOException {  
        SocketChannel socketChannel = (SocketChannel) key.channel();  
        Event event = new Event(socketChannel);  
        eventHandler.handleEvent(event);  
    }  
}
```

### Selector(Dispatcher)
- 비동기 이벤트를 모니터링
- 발생한 이벤트를 처리할 수 있는 채널 관리

```java
public abstract class Selector implements Closeable {  
  
    /**/    
	protected Selector() { }  
	
	/**  
	* Opens a selector.     *     * <p> The new selector is created 
	*/    
	public static Selector open() throws IOException {  
		return SelectorProvider.provider().openSelector();  
	}  	
	public abstract Set<SelectionKey> selectedKeys();   
	public abstract int select() throws IOException;  
	... 
}
```

### Handlers
- 비즈니스 로직
- 실제 작업을 수행
- 응답성 유지를 위해 CPU 작업을 작게, 잘게 또개서 분할해야 함
- IO Wait 작업이 필요하다면, 다른 스레드에서 수행 (IO작업 대기시간동안 이벤트 루프 block)

```java
public class EventHandler {  
    public void handleEvent(Event event) {  
        //비즈니스 로직
    }  
}
```

---

# 연결문서
- [Thread](../../servercommon/servercommon-Thread)
- [UML Diagram](../../developcommon/developcommon-UML-Diagram)