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
  
---
  
> **Reactor 패턴이란?**  
>
> Event Driven Application 에서 효율적인 IO와 멀티플렉싱을 제공하는 설계 패턴을 뜻한다. 
{: .notice--info}  

 Reactor 패턴은 **싱글 스레드**로 **요청 데이터를 순차 처리**하는 구조를 가지고 있다. 그리고 이벤트 처리를 **비동기**적으로 수행하기 때문에 효율적인 IO를 수행한다.

 간단하게 Reactor의 이벤트 처리 프로세스를 살펴보자.
 먼저 이벤트에 반응할 **reactor를 생성**하고 이벤트를 처리할 **event handler 등록**한다. 이후 reactor는 **이벤트가 발생할때까지 대기**하고 **이벤트가 수신되면 selector를 통해 handler에게 이벤트를 전달**한다.

 Reactor의 구성요소는 **Reactor**, **EventHandler**, **Selector**가 있다. 각각의 요소에 대해서 알아보자.
  
![image](../../assets/images/ReactorStructure.png)
  
## Reactor
 **이벤트를 전방에서 수신**하는 요소로 EventType과 EventHandler를 맵핑하여 가지고 있다. 
  
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
{: .notice}  
            Iterator<SelectionKey> keyIterator = selectedKeys.iterator();   
{: .notice}  
  
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
  
## Selector(Dispatcher)
 **비동기 이벤트를 모니터링**하고, **발생한 이벤트를 처리할 채널을 관리**하는 요소이다.
  
```java
public abstract class Selector implements Closeable {  
  
    /**/    
	protected Selector() { }  
	
	/**  
	* Opens a selector.     *     * <p> The new selector is created  
{: .notice}  
	*/    
	public static Selector open() throws IOException {  
		return SelectorProvider.provider().openSelector();  
	}  	
	public abstract Set<SelectionKey> selectedKeys();    
{: .notice}  
	public abstract int select() throws IOException;  
	... 
}
```
  
## Handlers
 실제 **비즈니스 로직을 수행**하는 요소로, 응답성 유지를 위해서 CPU 작업을 자게, 잘게 쪼개서 분할해야 한다. IO Wait 작업이 필요하다면, 다른 스레드에서 수행하도록 로직을 분할해야 한다. (IO작업 대기시간동안 이벤트 루프 block)
  
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