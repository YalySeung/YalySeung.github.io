---
title : "@Service"
excerpt : "@Service"
toc : true
toc_sticky : true
toc_label : "@Service"
categories:
- Annotation
tags:
- [Spring, Annotation]
last_modified_at: 2024-04-14T08:00:00-10:00:00
---
  
---
  
## Artifact
- org.springframework.stereotype
  
## 역할
- java 비즈니스 로직을 구현하는 Class를 명시
- 저장소 계층을 사용
  
## 사용법
  
```java
@Service  
public class BeanUtil implements ApplicationContextAware {  
  
    private static ApplicationContext context;  
  
    @Override  
    public void setApplicationContext(ApplicationContext applicationContext) throws BeansException {  
       context = applicationContext;  
    }  
  
    public static <T> T getBean(Class<T> beanClass) {   
{: .notice}  
       return context.getBean(beanClass);  
    }  
  
}
```

---
  
# 연결문서
- [@Component](../../annotation/annotation-@Component)
- [@Controller](../../annotation/annotation-@Controller)
- [@Repository](../../annotation/annotation-@Repository)