---
title : "Recoil"
excerpt : "Recoil"
toc : true
toc_sticky : true
toc_label : "Recoil"
categories:
- ReactStudy
tags:
- [React]
last_modified_at: 2024-05-04T08:00:00-10:00:00
---
  
---
  
> **Recoil 이란?**  
>
> Facebook에서 개발한 상태 관리 라이브러리로, React 애플리케이션에서 사용하기 위해 설계되었다. 
{: .notice--info}  
  
## Recoil의 특징
 Recoil은 React의 전역 상태 관리를 위해 설계된 라이브러리로, 기존 `useState`, `useContext` 등을 대체할 수 있다. Redux와 비교했을 때 설정이 간단하며, React와 완벽하게 통합된다.

 Recoil의 주요 특징은 다음과 같다.

 - **전역 상태 관리 지원** → Redux 없이도 간편하게 글로벌 상태 공유 가능
 - **React와 완벽한 호환** → 별도의 Provider 없이 사용 가능
 - **선언적 방식** → `atom`과 `selector`를 사용하여 상태를 관리
 - **비동기 지원** → `selector`를 활용하여 비동기 데이터를 쉽게 처리
  
## Recoil 기본 개념
  
### Atom (전역 상태)
 Recoil에서 `atom`은 전역 상태를 저장하는 단위이며, 컴포넌트에서 `useRecoilState()`를 사용하여 값을 읽고 업데이트할 수 있다.
  
```javascript
import { atom } from 'recoil';

export const countState = atom({
  key: 'countState', // 전역 상태의 고유 키
  default: 0,        // 초기값
});
```
  
### Selector (파생 상태)

`selector`는 `atom`의 값을 가공하거나, 비동기 데이터를 로딩할 때 사용한다.
  
```javascript
import { selector } from 'recoil';
import { countState } from './atoms';

export const doubleCountState = selector({
  key: 'doubleCountState',
  get: ({ get }) => get(countState) * 2,
});
```
  
### 상태 사용 (`useRecoilState`, `useRecoilValue`)

 Recoil 상태를 컴포넌트에서 사용할 때 `useRecoilState()` 또는 `useRecoilValue()`를 활용한다.
  
```javascript
import { useRecoilState, useRecoilValue } from 'recoil';
import { countState, doubleCountState } from './atoms';

function Counter() {
  const [count, setCount] = useRecoilState(countState);
  const doubleCount = useRecoilValue(doubleCountState);

  return (
    <div>
      <p>Count: {count}</p>
      <p>Double Count: {doubleCount}</p>
      <button onClick={() => setCount(count + 1)}>+</button>
    </div>
  );
}
```
  
## Recoil과 Redux 비교

 Recoil과 Redux는 전역 상태 관리를 제공하지만, 설정 방식과 사용 방법에서 차이가 있다.

|기능|Recoil|Redux|
|---|---|---|
|설정 과정|간단한 `atom`, `selector` 정의|Redux store, reducer 필요|
|전역 상태 관리|`useRecoilState()`로 간편 사용|`useSelector`, `useDispatch` 필요|
|비동기 지원|내장 `selector`로 간단히 처리|`redux-thunk` 같은 미들웨어 필요|
|학습 곡선|상대적으로 쉬움|비교적 복잡함|
  
## Recoil의 장점과 단점
  
### 장점
- React와 완벽한 호환 (별도 Provider 불필요)
- 코드가 간결하고 유지보수가 쉬움
- 비동기 상태 관리를 간편하게 처리 가능
  
### 단점
- 상태 변경이 많을 경우 성능 이슈 발생 가능
- 커뮤니티와 플러그인이 Redux보다 적음
- React 외 다른 프레임워크와 사용 어려움

---
  
# 연결문서
