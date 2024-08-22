---
title : "TestDouble"
excerpt : "TestDouble"
toc : true
toc_sticky : true
toc_label : "TestDouble"
categories:
- TDD
tags:
- [CleanCode, TDD]
last_modified_at: 2023-11-06T08:00:00-10:00:00
---
  
---
  
> **TestDouble이란?**  
>
> 단위 테스트를 진행하기 어려운 경우 이를 대신해 테스트를 진행할 수 있도록 만들어주는 객체를 의미한다. 
{: .notice--info}  

 테스트 자동화에서 여러 객체들이 **의존성을 가지고 있는 경우 테스트하는데 어려움이 있다**. 예를 들어 고객정보를 조회하는 API는 Database에 의존한다. 이런 경우 Database의 상태에 따라 테스트 결과가 달라질 수 있다. 반면에 **의존 관계가 간단한 경우 테스트 대상에만 집중**할 수 있다. **TestDouble**은 이런 **의존관계를 줄여주는 역할**을 한다.
  
## TestDouble의 종류
 TastDouble은 크게 **Dummy**, **Fake**, **Stub**, **Spy**, **Mock** 5가지로 나뉜다.
 
 **Dummy**는 가장 기본적인 TestDouble로 **인스턴스화 된 객체가 필요**하지만 **기능은 필요하지 않을 경우** 사용한다. Dummy 객체의 **메서드는 보통 아무런 동작을 하지 않는다**. 아래 코드는 Dummy TestDouble의 샘플 소스 이다.
  
```java
public class PrintWarningDummy implements PrintWarning {
    @Override
    public void print() {
        // 아무런 동작을 하지 않는다.
    }
}
```
  
 **Fake**는 복잡한 로직이나 객체 내부에서 필요로 하는 다른 외부 객체들의 **동작을 단순화하여 구현한 객체**이다. 동작의 **구현은 필요하지만**, 실제, **프로덕션에는 영향을 주지 않아야 할 때**, Fake를 사용한다. 아래 소스코드로 Database 관련 테스트에 적용해보자. 
  
```java
public class FakeUserRepository implements UserRepository {
    private Collection<User> users = new ArrayList<>();
    
    @Override
    public void save(User user) {
        if (findById(user.getId()) ** null) {
            user.add(user);
        }
    }
    
    @Override
    public User findById(long id) {
        for (User user : users) {
            if (user.getId() ** id) {
                return user;
            }
        }
        return null;
    }
}
```
  
 **Stub**는 객체가 **실제 동작하는 것처럼 보이게 만들어 놓은 객체**를 뜻한다. 호출 시, 입력에 상관없이 **미리 정해진 결과를 반환**하며, 일반적으로 매우 간단한 형태를 갖는다.
  
```java
public class StubUserRepository implements UserRepository {
    @Override
    public User findById(long id) {
        return new User(id, "Test User");
    }
}
```
  
 **Spy**는 **Stub** + **호출된 내용에 대한 약간의 정보를 기록**하는 객체로, 특정 객체의 동작을 관찰할때 사용하면 좋다.
  
```java
public class MailingService {
    private int sendMailCount = 0;
    private Collection<Mail> mails = new ArrayList<>();

    public void sendMail(Mail mail) {
        sendMailCount++;
        mails.add(mail);
    }

    public long getSendMailCount() {
        return sendMailCount;
    }
}
```
  
 **Mock**은 **호출에 대한 기대를 명세**하고 **내용에 따라 동작**하도록 프로그래밍 된 객체이다. Mock은 외부 의존성을 완전히 제거하고,  실제 객체를 완전히 대체할 수 있는 수단이다.
  
```java
@ExtendWith(MockitoExtension.class)
public class UserServiceTest {
    @Mock
    private UserRepository userRepository;
    
    @Test
    void test() {
        when(userRepository.findById(anyLong())).thenReturn(new User(1, "Test User"));
        
        User actual = userService.findById(1);
        assertThat(actual.getId()).isEqualTo(1);
        assertThat(actual.getName()).isEqualTo("Test User");
    }
}
```

---
  
# 연결문서
- 