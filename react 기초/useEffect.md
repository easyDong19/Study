# useEffect

## useEffect

컴포넌트가 마운트 됐을 때, 언마운트 됐을 때 업데이트 될 때 특정 작업을 처리할 때 사용

```jsx
function useEffect(effect: EffectCallback, deps?: DependencyList): void;
```

deps 배열을 비우게 된다면 컴포넌트가 처음 나타날 때에만 등록한 함수가 호출 된다.

useEffect는 함수를 반환 할 수 있는데, 이를 clean up 함수라 부른다. 

deps배열에 특정 값이 있다면 처음 마운트 될때와, 지정한 값이 바뀔 때도 호출 되고 

언마운트 될 때와 값이 바뀌기 직전에도 호출된다.

마운트시 하는 작업

- prop로 받은 값을 컴포넌트의 로컬 상태로 설정
- 외부 API 요청
- 라이브러리 사용
- SetInterval을 통한 반복 작업 혹은 setTimeout을 통한 작업 예약

언마운트시 하는 작업

- setInterval, setTimeout을 사용하여 등록한 작업 clear
- 라이브러리 인스턴스 제거

useEffect 안에서 사용하는 상태나, props가 있다면, useEffect deps에 넣어주어야 한다.

만약 deps 파라미터를 생략한다면 컴포넌트가 리렌더링 될 때마다 호출이 된다.

리액트에선 부모 컴포넌트가 리렌더링 → 자식또한 리렌더링(even 바뀐 내용 없음)