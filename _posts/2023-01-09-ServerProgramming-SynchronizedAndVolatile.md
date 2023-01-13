---
title: "synchronized And volatile"
excerpt: "공유 자원 동기화"

categories:
- ServerProgramming 

tags:
- [ServerProgramming]

toc: true
toc_sticky: true
toc_label: "synchronized And volatile"
last_modified_at: 2023-01-10T08:00:00-10:00:00
---

# 공유자원 동기화의 필요성 
  - 멀티 스레드 환경에서 여러 스레드가 공유자원에 접근할 때, 데이터의 일관성을 위해 동기화 처리가 필요하다.

---

# Volatile 키워드
## Single Thread vs Multi Thread
  ![image](/assets/images/ServerProgramming/ValueHandling_Single_Multi_Thread.png)  

## Volatile 이란?
  - 변수를 Main Memory에 저장하겠다는 명시적 표현
  - 일반 변수의 값은 CPU cache에 저장되지만, Volatile로 선언된 변수의 값은 Main Memory 에 Read/Write 된다.

## Volatile의 필요성
  - MultiThread 어플리케이션에서 일반 변수를 사용하면, CPU cache에서 값을 Read/Write 하기때문에 변수값이 불일치 하는 상황이 발생
  - 1개의 Write Transaction와 1개 이상의 Read Transaction를 사용할 경우, 값의 무결성을 보장한다.

---

# synchronized 키워드
  - Main Memory의 값 동기화를 위해 사용
  - example) 공유자원 number의 값을 1 증가시키는 멀티스레드 프로그램을 예시로 synchronized 키워드에 대해 알아보자.

## 테스트 소스 구조
  ![image](/assets/images/ServerProgramming/SynchronizedSource_ClassDiagram.png)  

---

## number 값 증가
  ```java
  public abstract class AddOneTestBase {
    public void AddOne(NumberTableClass numberTable){
        int currentNumber = numberTable.getNumber();

        WaitOneSec();

        numberTable.setNumber(currentNumber + 1);
    }

    private void WaitOneSec() {
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }
    }
  }
  ```
  - 공유자원의 변화를 확인하기 위해 getter와 setter 사이에 sleep 적용

## multiThread 생성 및 실행
  ```java
  public class ClassTester<T> {
    private T testClass;

    public ClassTester(T testClass) {
        this.testClass = testClass;
    }

    public void startMultiThread(NumberTableClass numberTable) {

        Thread thread1 = getThread(numberTable);
        Thread thread2 = getThread(numberTable);

        try {
            thread1.start();
            thread2.start();

            thread1.join(3000);
            thread2.join(3000);
        } catch (InterruptedException e) {
            throw new RuntimeException(e);
        }
    }

    private Thread getThread(NumberTableClass numberTable) {
        return new Thread(() -> {
            Method method;
            try {
                method = testClass.getClass().getMethod("Do", NumberTableClass.class);
                method.invoke(testClass, numberTable);
            } catch (NoSuchMethodException e) {
                throw new RuntimeException(e);
            } catch (InvocationTargetException e) {
                throw new RuntimeException(e);
            } catch (IllegalAccessException e) {
                throw new RuntimeException(e);
            }
        });
    }
  }
  ```
---

## synchronized method
  ```java
  public class SynchronizedMethodClass extends AddOneTestBase{
      public synchronized void Do(NumberTableClass numberTable){
          AddOne(numberTable);
      }
  }
  ```
  - 인스턴스 단위로 공유자원에 대한 접근을 잠금/해제한다.
  - 메서드에 synchronized 키워드 적용

---

## static synchronized method
  ```java
  public class StaticSynchronizedMethodClass extends AddOneStaticTestBase{
    public static synchronized void Do(NumberTableClass numberTable){
        AddOne(numberTable);
    }
  }
  ```
  - 클래스 단위로 공유자원에 대한 접근을 잠금/해제한다.
  - 메서드에 synchronized 키워드 적용

---

## synchronized block
  ```java
  public void Do(NumberTableClass numberTable){
    synchronized (this){
        AddOne(numberTable);
    }
  }
  ```
  - 인스턴스 단위로 공유자원에 대한 접근을 잠금/해제한다.
  - 메서드 내 특정 범위에 synchronized 키워드 적용

---

## static synchronized block
  ```java
  public class StaticSynchronizedBlockClass extends AddOneStaticTestBase{
    public static void Do(NumberTableClass numberTable){
        synchronized (StaticSynchronizedBlockClass.class){
            AddOne(numberTable);
        }
    }
  }
  ```
  - 클래스 단위로 공유자원에 대한 접근을 잠금/해제한다.
  - 메서드 내 특정 범위에 synchronized 키워드 적용


