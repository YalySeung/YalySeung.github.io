---
title : "Stream"
excerpt : "Stream"
toc : true
toc_sticky : true
toc_label : "Stream"
categories:
- java
tags:
- [java]
last_modified_at: 2024-04-23T08:00:00-10:00:00
---
  
---
  
> **Stream이란**  
>
> Collection에 저장되어 있는 Element를 하나씩 순회하면서 처리할 수 있는 API를 뜻한다. 
{: .notice--info}  

> **지연평가란?**  
>
> Stream 생성 시점에 연산이 바로 수행 되는 것이 아니라 최종 연산이 호출될 때까지 연산이 지연된다. 이러한 특성은 필요한 연산만을 실행하여 효율적이다. 
{: .notice--info}  

 우선 Stream을 생성하는 방법부터 알아보자. **List에서 가져오기**, **Array에서 가져오기**, **builder로 생성하기**, **generate로 생성하기** 등의 방법이 있다.
  
```java
List<String> userList = Arrays.asList("철수", "영희", "동수"); 
{: .notice--info}  
Stream<String> userStream = list.stream(); 
{: .notice}  
```
  
```java
String[] userArray = new String[]{"철수", "영희", "동수"};
Stream<String> userStream = Arrays.stream(array); 
{: .notice}  
```
  
```java
String<String> userStream = Stream<String>builder() 
{: .notice}  
						.add("철수")
						.add("영희")
						.add("동수")
						.build();
```
  
```java
// 무한한 난수를 생성하는 스트림 생성
Stream<Integer> randomStream = Stream.generate(() -> new Random().nextInt()); // 무한한 난수 스트림에서 처음 10개의 요소를 출력 
{: .notice}  
randomStream.limit(10).forEach(System.out::println);
```
 generate() 함수는 일반적으로 **무한한 요소를 생성**하는 Stream을 만들 때 사용한다.

> **caution**
>
> generate() 메서드는 Supplier를 사용하는데, Supplier 는 상태가 없어야하고, 호출할 때마다 새로운 값을 생성해야한다. 그렇지 않으면 무한루프에 빠질 가능성이 있으므로 주의하자. 
{: .notice}  
  
## Stream Method
 Stream을 생성했으니 Stream의 Method에 대해서 알아보자

| method명  | 기능                            |
| -------- | ----------------------------- |
| concat   | Merge Stream                  |
| filter   | 특정 Item만 선별                   |
| map      | Item의 특정 값또는 값을 변환하여 반환       |
| sorted   | Stream Item을 정렬               |
| peek     | 데이터를 변현하지 않고 인자로 받은 람다식만 수행   |
| count    | Item의 개수를 반환                  |
| sum      | Item의 합을 반환                   |
| collect  | stream 데이터를 Collection 형태로 반환 |
| foreEach | Item으로 반복문 수행                 |

 Method를 활용한 예시를 살펴보겠다.
  
```java
Stream<String> numberStream = Stream.iterate(1, n -> n + 1).limit(5); 
{: .notice}  
// => {1,2,3,4,5} 
{: .notice}  
```
  
```java
//Item 출력
Stream<String> numberStream = Stream.foreEach(item -> System.out.println(item); 
{: .notice}  
```
  
---
  
# 연결문서
