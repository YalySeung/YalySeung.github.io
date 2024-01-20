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

# 날짜 : 2023-11-06 16:18

# 태그 : #CleanCode #TDD
---

# 내용

## TestDouble이란
> 테스트를 진행하기 어려운 경우 이를 대신해 테스트를 진행할 수 있도록 만들어주는 객체를 의미한다.
{: .notice--info}

## TestDouble로 대체할 대상
- Database
- API

## TestDouble의 종류

### Dummy
- 가장 기본적인 TestDouble
- 인스턴스화된 객체가 필요하지만 기능은 필요하지 않을 경우 사용
- Dummy 객체의 메서드는 정상동작을 보장하지 않는다

```java
public class PrintWarningDummy implements PrintWarning {
    @Override
    public void print() {
        // 아무런 동작을 하지 않는다.
    }
}
```

### Fake
- 복잡한 로직이나 객체 내부에서 필요로 하는 다른 외부 객체들의 동작을 단순화하여 구현한 객체
- 동작의 구현을 가지고 있지만 실제 프로덕션에는 적합하지 않은 객체
- Fake 데이터베이스 필요시 사용

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

### Stub
- 객체가 실제 동작하는 것처럼 보이게 만들어놓은 객체
- 인터페이스 또는 기본 클래스가 최소한으로 구현된 상태

```java
public class StubUserRepository implements UserRepository {
    @Override
    public User findById(long id) {
        return new User(id, "Test User");
    }
}
```

### Spy
- Stub의 기능 + 호출된 내용에 대한 약간의 정보를 기록
- 실제 객체처럼 동작
- 필요한 부분에서는 Stub처럼 동작

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

### Mock
- 호출에 대한 기대를 명세하고 내용에 따라 동작하도록 프로그래밍 된 객체

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