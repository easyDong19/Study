# useReducer

## useReducer

useState만으로는 상태를 관리하기 복잡할 때 사용

컴포넌트의 상태 업데이트 로직을 컴포넌트에서 분리시킬 수 있음

### reducer

```jsx
function reducer(state, action) {
  // 새로운 상태를 만드는 로직
  // const nextState = ...
  return nextState;
}
```

현재 상태와 액션 객체를 파라미터로 받아와서 새로운 상태로 반환해주는 함수

### action

업데이트를 위한 정보를 가지고 있음. 주로 type 값을 지닌 객체 형태로 사용

```jsx
// 새 할 일을 등록하는 액션
{
  type: 'ADD_TODO',
  todo: {
    id: 1,
    text: 'useReducer 배우기',
    done: false,
  }
}
```

## useReducer 사용 방법

```jsx
const [state, dispatch] = useReducer(reducer, initialState);
```

## 번외 커스텀HOOK

```jsx
import { useCallback, useReducer } from 'react';

function reducer(state, action) {
  switch (action.type) {
    case 'CHANGE':
      return {
        ...state,
        [action.name]: action.value,
      };
    case 'RESET':
			//개인적으로 진짜 감탄한 코드//
      return Object.keys(state).reduce((acc, current) => {
        acc[current] = '';
        return acc;
      }, {});
    default:
      return state;
  }
}

function useInputs(initialForm) {
  const [form, dispatch] = useReducer(reducer, initialForm);
  // change
  const onChange = useCallback((e) => {
    const { name, value } = e.target;
    dispatch({ type: 'CHANGE', name, value });
  }, []);
  const reset = useCallback(() => dispatch({ type: 'RESET' }), []);
  return [form, onChange, reset];
}

export default useInputs;
```