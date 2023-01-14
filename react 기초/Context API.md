# Context API

## Context API

프로젝트 안에서 전역적으로 사용할 수 있는 값을 관리 할 수 있다.

이 값은 상태, 함수, 외부 라이브러리 인스턴스, DOM 일 수도 있음

```jsx
const UserDispatch = React.createContext(null);
```

사용하기 위해선

```jsx
<UserDispatch.Provider value={dispatch}>...</UserDispatch.Provider>
```

Provider 컴포넌트에 value로 지정해주면 된다.

Provider에 의하여 감싸진 컴포넌트들은 Context 값을 어디서나 사용할 수 있게 된다.

```jsx
const dispatch = useContext(UserDispatch);
```