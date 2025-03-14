---
title : "React Query(Tanstack Query)"
excerpt : "React Query(Tanstack Query)"
toc : true
toc_sticky : true
toc_label : "React Query(Tanstack Query)"
categories:
- ReactStudy
tags:
- [React]
last_modified_at: 2024-05-03T08:00:00-10:00:00
---
  
---
  
> **React Query란?**  
>
>  React 애플리케이션에서 서버 상태를 관리하기 위한 라이브러리이다. 
{: .notice--info}  

  React Query(Tanstack Query)는 **API 요청과 캐싱을 간편하게 처리하여 상태 관리를 최적화할 수 있도록 도와준다.**
  
## 설치
  
```bash
npm install @tanstack/react-query
```
  
## 사용법
  
### 1️⃣ 기본적인 `useQuery` 사용 예제
  
```javascript
import { useQuery } from "@tanstack/react-query";

const fetchUser = async () => {
    const response = await fetch("https://api.example.com/user");
    return response.json();
};

const UserComponent = () => {
    const { data, isLoading, error } = useQuery({ queryKey: ["user"], queryFn: fetchUser });

    if (isLoading) return <p>Loading...</p>;
    if (error) return <p>Error: {error.message}</p>;

    return <p>User: {data.name}</p>;
};
```
  
### 2️⃣ `useMutation`을 활용한 데이터 변경
  
```javascript
import { useMutation } from "@tanstack/react-query";

const updateUser = async (userData) => {
    const response = await fetch("https://api.example.com/user", {
        method: "POST",
        body: JSON.stringify(userData),
    });
    return response.json();
};

const UserUpdateComponent = () => {
    const mutation = useMutation(updateUser);

    return (
        <button onClick={() => mutation.mutate({ name: "New Name" })}>
            Update User
        </button>
    );
};
```
  
## 장점과 단점
  
### ✅ 장점
- **자동으로 API 응답을 캐싱하여 불필요한 요청 방지**  
- **API 요청 실패 시 자동 재시도 기능 제공**  
- **데이터 동기화 및 상태 업데이트 간소화**  
  
### ❌ 단점
- **기본적인 상태 관리 도구보다 상대적으로 학습 곡선이 높을 수 있음**  
- **작은 프로젝트에서는 불필요한 오버헤드가 발생할 가능성 있음**  

---
  
# 연결문서
