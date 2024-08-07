# React

- 리액트란?
  - 사용자 인터페이스를 만들기 위한 자바스크립트 라이브러리
  - 컴포넌트(component)라는 재사용 가능한 코드를 이용해 UI 구성
  - JSX(JavaScript XML)라는 문법 사용
    > **JSX 코드**: 자바스크립트 파일에 작성된 HTML 코드
    - JSX 요소는 HTML과 마찬가지로 속성을 가지며 서로 중첩 가능
    - JSX는 정확히 하나의 부모 태그를 가져야 하며, 다른 요소는 내부에 중첩 가능
    - react-dom/client에서 createRoot()를 사용하여 지정된 DOM 요소에 React 루트를 만들 수 있다.
    - React root의 render() 메서드를 사용하여 화면에서 JSX를 렌더링할 수 있다.
    - React root의 render() 메서드는 가상 DOM을 사용하여 변경된 DOM 요소만 업데이트한다.
  - 빌드 프로세스를 사용
    - 리액트 코드는 특별한 JSX 기능을 사용한다. JSX 코드는 기본적으로 표준 자바스크립트 기능이 아니므로 정상 작동하지 않기 때문에 빌드 과정을 통해 코드를 변환해야 브라우저에서 실행할 수 있다.
    - 리액트 라이브러리를 통해 작성한 코드는 프로덕션을 위해 최적화되지 않았다. vite, create-react-app과 같은 도구를 이용해 프로젝트에 빌드 프로세스를 포함하여 생성할 수 있다.
- react 기본

  - 컴포넌트
    - 리액트에서 UI를 구성하는 기본 단위
    - 재사용 가능한 코드 블록으로, 하나의 독립적인 UI 요소를 표현
    - 재사용할 수 있으며, 코드가 분리되어 있기 때문에 유지보수가 용이
  - props

    - “properties”의 줄임말로, 컴포넌트 간에 데이터를 전달할 때 사용하는 객체
    - 부모 컴포넌트가 자식 컴포넌트에 데이터를 전달하고자 할 때 사용
    - 자식 컴포넌트에서는 변경할 수 없는 읽기 전용 데이터
    - props는 숫자, 문자열, 배열, 객체, 함수 등 다양한 타입의 데이터를 전달할 수 있음

    ```jsx
    // 부모 컴포넌트 (ParentComponent)

    import React from "react";
    import ChildComponent from "./ChildComponent";

    function ParentComponent() {
      const userName = "Alice";
      const userAge = 25;

      return (
        <div>
          <h1>부모 컴포넌트</h1>
          <ChildComponent name={userName} age={userAge} />
        </div>
      );
    }

    export default ParentComponent;
    ```

    ```jsx
    // 자식 컴포넌트 (ChildComponent)

    import React from "react";

    function ChildComponent(props) {
      return (
        <div>
          <p>
            안녕하세요, 제 이름은 {props.name}이고, 나이는 {props.age}살입니다.
          </p>
        </div>
      );
    }

    export default ChildComponent;
    ```

- State Hook

  - state
    - 리액트 컴포넌트 내에서 동적으로 변할 수 있는 데이터
    - 컴포넌트가 직접 상태를 변경 가능
    - 컴포넌트가 상태를 관리하고, 상태가 변경되면 리액트가 해당 컴포넌트를 다시 렌더링하여 UI를 최신 상태로 유지
    - 함수형 컴포넌트에서는 **useState**라는 리액트 훅을 사용하여 상태를 관리
      > **리액트 훅(Hooks) -** 함수형 컴포넌트에서 상태와 생명주기 메서드 등의 기능을 사용할 수 있게 해주는 특별한 함수
      - 함수형 컴포넌트 또는 사용자 정의 훅 내부에서만 사용
      - 반드시 함수 컴포넌트의 최상위에서 호출
      - 루프, 조건문, 또는 중첩된 함수 내에서 훅 호출 불가
        >
  - useState

    - 두 가지 값을 가진 배열을 반환
    - 첫 번째 요소는 현재 상태값, 두 번째 요소는 상태를 변경하는 함수

      ```jsx
      import React, { useState } from "react";

      function Example() {
        // 상태 변수와 상태를 업데이트하는 함수 선언
        const [count, setCount] = useState(0);

        return (
          <div>
            <p>현재 카운트: {count}</p>
            <button onClick={() => setCount(count + 1)}>증가</button>
          </div>
        );
      }

      export default Example;
      ```

      - `useState`는 배열을 반환하며, 첫 번째 요소는 현재 상태 값(`count`), 두 번째 요소는 상태를 변경하는 함수(`setCount`)이다.
      - `useState(0)`은 초기 상태 값을 `0`으로 설정한다.
      - 상태를 변경하려면 `setCount` 함수를 호출하면 된다. 예를 들어, 버튼을 클릭하면 `setCount(count + 1)`에 의해 `count` 값이 1 증가하고 UI가 자동으로 업데이트된다.

    - `useState`는 단순한 숫자뿐 아니라, 문자열, 객체, 배열 등 다양한 타입의 상태 관리 가능

      ```jsx
      import React, { useState } from "react";

      function UserProfile() {
        const [user, setUser] = useState({ name: "", age: 0 });

        const updateName = (e) => setUser({ ...user, name: e.target.value });
        const updateAge = (e) =>
          setUser({ ...user, age: Number(e.target.value) });

        return (
          <div>
            <input
              type="text"
              placeholder="이름"
              value={user.name}
              onChange={updateName}
            />
            <input
              type="number"
              placeholder="나이"
              value={user.age}
              onChange={updateAge}
            />
            <p>{`사용자: ${user.name}, 나이: ${user.age}`}</p>
          </div>
        );
      }
      ```

      - `user` 객체를 상태로 사용하고, 입력 필드를 통해 이름과 나이를 업데이트한다.
      - 상태가 객체일 때는 상태를 변경할 때 기존 상태를 복사하여 필요한 부분만 업데이트하는 방식으로 관리한다.

    - `useState`의 상태 업데이트는 비동기적으로 처리된다. 따라서, 여러 상태 업데이트가 동시에 발생하거나, 여러 업데이트가 순차적으로 일어나면서 예상치 못한 결과가 생길 수 있기 때문에 콜백 함수를 사용하는 것이 좋다.

      - 예시(상태 업데이트에서 콜백 함수가 필요한 상황)

        ```jsx
        import React, { useState } from "react";

        function Counter() {
          const [count, setCount] = useState(0);

          const incrementTwice = () => {
            // 상태를 업데이트하기 위해 이전 상태를 참조하는 함수
            setCount((prevCount) => prevCount + 1);
            setCount((prevCount) => prevCount + 1);
          };

          return (
            <div>
              <p>현재 카운트: {count}</p>
              <button onClick={incrementTwice}>두 번 증가</button>
            </div>
          );
        }
        ```

        - 위 코드에서 `incrementTwice` 함수는 버튼을 클릭하면 `count`를 두 번 증가시킨다. 만약 콜백 함수를 사용하지 않고 단순히 상태 값을 직접 설정하면 문제가 발생할 수 있다.

        ```jsx
        const incrementTwice = () => {
          setCount(count + 1);
          setCount(count + 1);
        };
        ```

        - 위의 경우, 첫 번째 `setCount(count + 1)`이 실행될 때 `count`는 현재 값에서 1만 증가하게 되고, 두 번째 `setCount(count + 1)`도 여전히 같은 현재 값을 참조하기 때문에 `count`는 총 1만 증가하게 된다. 하지만 콜백 함수를 사용하면 상태 업데이트가 순차적으로 올바르게 처리된다.

- Ref Hook

  - useRef

    - 렌더링에 필요하지 않은 값을 참조할 수 있는 React Hook
    - `useRef(initialValue)`
      - 매개변수 `initialValue`: ref 객체의 `current`프로퍼티 초기 설정값으로, 여기에는 어떤 유형의 값이든 지정할 수 있다. 이 인자는 초기 렌더링 이후부터는 무시된다.
      - 반환값: `useRef`는 단일 프로퍼티를 가진 객체를 반환
        - `current`: 처음에는 전달한 `initialValue`로 설정되며 나중에 다른 값으로 바꿀 수 있다. ref 객체를 JSX 노드의 `ref` 속성으로 React에 전달하면 React는 `current`프로퍼티를 설정한다.
      - 다음 렌더링에서 `useRef`는 동일한 객체를 반환한다.
    - ref를 변경해도 리렌더링을 촉발하지 않는다.
    - ref를 사용하여 DOM을 조작하는 것이 일반적이다.

      ```jsx
      // 텍스트 input에 초점 맞추기

      import { useRef } from "react";

      export default function Form() {
        const inputRef = useRef(null);

        function handleClick() {
          inputRef.current.focus();
        }

        return (
          <>
            <input ref={inputRef} />
            <button onClick={handleClick}>Focus the input</button>
          </>
        );
      }
      ```

    - 컴포넌트 안에서 조회 및 수정 할 수 있는 변수를 관리할 수 있다.
      - `useRef` 로 관리하는 변수는 값이 바뀐다고 해서 컴포넌트가 리렌더링되지 않는다. `useRef` 로 관리하고 있는 변수는 설정 후 바로 조회 할 수 있다.

- Effect Hook

  - effect
    - 컴포넌트가 렌더링(또는 다시 렌더링)될 때마다 무언가를 수행하도록 알려준다.
  - useEffect

    - 컴포넌트가 마운트 됐을 때 (처음 나타났을 때), 언마운트 됐을 때 (사라질 때), 그리고 업데이트 될 때 (특정 props가 바뀔 때) 특정 작업을 처리
    - 함수의 첫 번째 인수로는, 컴포넌트가 렌더링된 후에 실행할 콜백 함수 또는 특정 함수를 전달
    - 두 번째 인수로는, 배열을 전달
      - 두 번째 인수로 빈 배열을 넣으면, 컴포넌트가 처음 나타날 때에만 `useEffect`에 등록한 함수가 호출된다.
      - 두 번째 인수로 특정 값을 넣으면, 컴포넌트가 처음 마운트될 때와 배열의 주어진 상태 값들에 변화가 있을 경우에만 `useEffect`에 등록한 함수가 호출된다.
      - 두 번째 인수를 생략하면, 컴포넌트가 리렌더링될 때마다 `useEffect`에 등록한 함수가 호출된다.
    - `useEffect`는 Effect Hook을 사용하여 다른 함수를 호출하므로 반환 값이 없다.
    - 함수를 반환할 경우, `useEffect`는 항상 그것을 clean-up 함수로 취급
      - React는 컴포넌트가 리렌더링되거나 언마운트 되기 전에 이 clean-up 함수를 호출한다. clean-up 함수를 사용하게 되면 이전에 남은 함수가 실행되어 메모리 누수가 일어나는 일을 방지할 수 있다.

    ```jsx
    import React, { useEffect, useState } from "react";

    function WindowSize() {
      const [windowSize, setWindowSize] = useState({
        width: window.innerWidth,
        height: window.innerHeight,
      });

      useEffect(() => {
        // 윈도우 크기가 변경될 때 호출될 함수
        const handleResize = () => {
          setWindowSize({
            width: window.innerWidth,
            height: window.innerHeight,
          });
        };

        // 이벤트 리스너 등록
        window.addEventListener("resize", handleResize);

        // 클린업 함수: 컴포넌트가 언마운트될 때 이벤트 리스너 제거
        return () => {
          window.removeEventListener("resize", handleResize);
        };
      }, []); // 빈 배열을 의존성 배열로 사용하면 마운트 시에만 실행됨

      return (
        <div>
          <h1>Window Size</h1>
          <p>Width: {windowSize.width}px</p>
          <p>Height: {windowSize.height}px</p>
        </div>
      );
    }

    export default WindowSize;
    ```

- Memo Hook

  - 컴포넌트의 성능을 최적화하는 데 사용되는 Hook
  - Memo는 “memoized”를 의미하며, 이는 이전에 계산 한 값을 재사용한다는 의미
    > **Memoization -** 기존에 수행한 연산의 결과값을 어딘가에 저장해두고 동일한 입력이 들어오면 재활용하는 프로그래밍 기법
    - 중복 연산을 피할 수 있기 때문에 애플리케이션의 성능을 최적화할 수 있다.
      >
  - 특정 값이 변경되었을 때만 연산을 다시 수행하고, 그렇지 않으면 이전에 계산된 값을 재사용한다.
  - `useMemo` 의 첫 번째 인수에는 어떻게 연산할지 정의하는 함수를 넣어주고, 두 번째 인수에는 배열을 넣어준다. 이 배열 안의 값이 바뀌면 등록한 함수를 호출해서 값을 연산해주고, 값이 바뀌지 않았다면 이전에 연산한 값을 재사용한다.

  ```jsx
  import React, { useMemo, useState } from "react";

  function App() {
    const [count, setCount] = useState(0);
    const [value, setValue] = useState(0);

    const expensiveCalculation = (num) => {
      console.log("Calculating...");
      // 아주 복잡한 계산이라고 가정
      return num * 2;
    };

    // count가 변경될 때만 expensiveCalculation을 재실행
    const memoizedValue = useMemo(() => expensiveCalculation(count), [count]);

    return (
      <div>
        <h1>useMemo Example</h1>
        <p>Count: {count}</p>
        <p>Memoized Value: {memoizedValue}</p>
        <button onClick={() => setCount(count + 1)}>Increment Count</button>
        <button onClick={() => setValue(value + 1)}>Increment Value</button>
        <p>Value: {value}</p>
      </div>
    );
  }

  export default App;
  ```

- Callback Hook

  - 컴포넌트가 불필요하게 재렌더링되는 것을 방지하기 위해 특정 함수를 메모이제이션하는 훅
  - 첫 번째 인수에는 메모이제이션하려는 함수를 넣어주고, 두 번째 인수로는 의존성 배열을 넣어준다. 배열 안의 값들이 변경될 때만 함수가 새로 생성된다.

    ```jsx
    import React, { useState, useCallback } from "react";

    // 자식 컴포넌트
    const TodoItem = React.memo(({ todo, onToggle }) => {
      console.log("TodoItem rendered:", todo.text);
      return (
        <div>
          <input
            type="checkbox"
            checked={todo.completed}
            onChange={() => onToggle(todo.id)}
          />
          {todo.text}
        </div>
      );
    });

    // 부모 컴포넌트
    const TodoList = () => {
      const [todos, setTodos] = useState([
        { id: 1, text: "Learn React", completed: false },
        { id: 2, text: "Learn useCallback", completed: false },
      ]);

      const [count, setCount] = useState(0);

      // useCallback을 사용하여 onToggle 메모이제이션
      const onToggle = useCallback((id) => {
        setTodos((prevTodos) =>
          prevTodos.map((todo) =>
            todo.id === id ? { ...todo, completed: !todo.completed } : todo
          )
        );
      }, []);

      return (
        <div>
          <button onClick={() => setCount(count + 1)}>Re-render Parent</button>
          <p>Parent render count: {count}</p>
          {todos.map((todo) => (
            <TodoItem key={todo.id} todo={todo} onToggle={onToggle} />
          ))}
        </div>
      );
    };

    export default TodoList;
    ```

    - **상태 관리**: `TodoList` 컴포넌트는 `todos`와 `count` 상태를 관리
    - **`useCallback` 사용**: `onToggle` 함수는 `useCallback`을 사용하여 메모이제이션된다. 이 함수는 의존성 배열이 빈 배열(`[]`)이므로 컴포넌트가 처음 렌더링될 때만 생성되고 이후로는 동일한 함수를 계속 사용한다.
    - **`React.memo`**: `TodoItem` 컴포넌트는 `React.memo`로 감싸져 있어, 전달된 props가 변경되지 않는 한 재렌더링되지 않는다. 여기서 `onToggle` prop이 변경되지 않기 때문에 `todos` 상태가 변경되지 않는 한 `TodoItem`은 다시 렌더링되지 않는다.
    - **부모 컴포넌트의 재렌더링**: `Re-render Parent` 버튼을 클릭하면 `count` 상태가 증가하고 부모 컴포넌트가 재렌더링된다. 그러나 `onToggle` 함수는 재생성되지 않기 때문에 `TodoItem` 컴포넌트는 불필요하게 재렌더링되지 않는다.

- useMemo와 useCallback의 차이점
  - **`useMemo`**: 계산된 값을 메모이제이션한다. 즉, 값이 필요할 때만 계산을 다시 수행하고, 그렇지 않으면 이전에 계산된 값을 반환한다. 주로 무거운 계산을 피하기 위해 사용한다.
  - **`useCallback`**: 함수를 메모이제이션한다. 주로 컴포넌트가 다시 렌더링될 때마다 함수가 재생성되는 것을 방지하기 위해 사용한다.
- React.memo

  - 컴포넌트의 props가 변경되지 않는 한 컴포넌트를 다시 렌더링하지 않도록 하는 역할
  - 불필요한 렌더링을 피하여 성능을 최적화하는 데 유용하다.
  - 기본적으로 `React.memo`는 함수형 컴포넌트를 인수로 받아, 해당 컴포넌트가 동일한 props로 다시 렌더링되지 않도록 한다.

    ```jsx
    import React, { useState, memo } from "react";

    // 자식 컴포넌트
    const ChildComponent = memo(({ count }) => {
      console.log("ChildComponent rendered");
      return <p>Child Count: {count}</p>;
    });

    // 부모 컴포넌트
    const ParentComponent = () => {
      const [parentCount, setParentCount] = useState(0);
      const [childCount, setChildCount] = useState(0);

      return (
        <div>
          <button onClick={() => setParentCount(parentCount + 1)}>
            Increment Parent Count
          </button>
          <p>Parent Count: {parentCount}</p>
          <button onClick={() => setChildCount(childCount + 1)}>
            Increment Child Count
          </button>
          <ChildComponent count={childCount} />
        </div>
      );
    };

    export default ParentComponent;
    ```

    - **상태 관리**: `ParentComponent`는 `parentCount`와 `childCount` 두 개의 상태를 관리한다.
    - **`React.memo` 사용**: `ChildComponent`는 `React.memo`로 감싸져 있어, 전달된 `count` prop이 변경되지 않는 한 재렌더링되지 않는다.
    - **버튼 클릭 이벤트**: 두 개의 버튼이 각각 `parentCount`와 `childCount` 상태를 증가시킨다.
    - `Increment Parent Count` 버튼을 클릭하면 `parentCount` 상태가 변경되어 `ParentComponent`가 재렌더링된다. 하지만 `ChildComponent`의 `count` prop은 변경되지 않기 때문에 `ChildComponent`는 재렌더링되지 않는다.
    - `Increment Child Count` 버튼을 클릭하면 `childCount` 상태가 변경되어 `ChildComponent`의 `count` prop도 변경된다. 이때 `ChildComponent`는 재렌더링된다.

- Reducer Hook

  - 상태 관리를 위해 사용하는 훅
  - reducer는 현재 상태와 액션 객체를 파라미터로 받아와서 새로운 상태를 반환해주는 함수

  ```jsx
  const [state, dispatch] = useReducer(reducer, initialState);
  ```

  - 여기서 `state`는 우리가 앞으로 컴포넌트에서 사용할 수 있는 상태를 나타내고, `dispatch`는 액션을 발생시키는 함수를 의미한다.
  - `useReducer`에 넣는 첫 번째 인수는 reducer 함수로, 현재 상태와 액션을 인수로 받아 새로운 상태를 반환하는 함수이다.
  - 두 번째 인수는 초기 상태로, 상태의 초기값을 의미한다.
  - 세 번째 인수는 초기화 함수(선택 사항)로, 초기 상태를 생성하는 함수이고 초기 상태 계산이 복잡한 경우 사용한다.

    ```jsx
    import React, { useReducer } from "react";

    // 리듀서 함수
    const counterReducer = (state, action) => {
      switch (action.type) {
        case "increment":
          return { count: state.count + 1 };
        case "decrement":
          return { count: state.count - 1 };
        default:
          return state;
      }
    };

    // 초기 상태
    const initialState = { count: 0 };

    // 컴포넌트
    const Counter = () => {
      const [state, dispatch] = useReducer(counterReducer, initialState);

      return (
        <div>
          <p>Count: {state.count}</p>
          <button onClick={() => dispatch({ type: "increment" })}>
            Increment
          </button>
          <button onClick={() => dispatch({ type: "decrement" })}>
            Decrement
          </button>
        </div>
      );
    };

    export default Counter;
    ```

    - **리듀서 함수**: `counterReducer`는 현재 상태(`state`)와 액션(`action`)을 받아 새로운 상태를 반환한다. 여기서는 `increment`와 `decrement` 두 가지 액션 타입을 처리한다.
    - **초기 상태**: `initialState`는 `count`의 초기값을 0으로 설정한다.
    - **컴포넌트**: `Counter` 컴포넌트는 `useReducer` 훅을 사용하여 상태와 디스패치 함수를 반환받는다. `state`는 현재 상태를 나타내고, `dispatch`는 액션을 디스패치하는 함수이다.
    - **버튼 클릭 이벤트**: 각 버튼을 클릭하면 해당 액션 타입을 가진 객체를 `dispatch` 함수에 전달하여 상태를 업데이트한다.
    - `Increment` 버튼을 클릭하면 `{ type: 'increment' }` 액션이 디스패치되어 `counterReducer`가 호출되고, `state.count`가 1 증가한다.
    - `Decrement` 버튼을 클릭하면 `{ type: 'decrement' }` 액션이 디스패치되어 `counterReducer`가 호출되고, `state.count`가 1 감소한다.

- Custom Hook
  - 커스텀 훅은 재사용 가능한 로직을 캡슐화하여 여러 컴포넌트에서 쉽게 사용할 수 있도록 하는 함수
  - 상태 관리, 사이드 이펙트 처리 등을 수행하는 로직을 공통된 함수로 분리함으로써 코드의 중복을 줄이고 가독성을 높일 수 있다.
  - 커스텀 훅 만드는 방법
    - **훅의 이름**: 커스텀 훅은 항상 `use`로 시작해야 한다. 이는 리액트가 이 함수가 훅임을 인식할 수 있게 한다.
    - **리액트 훅 사용**: 커스텀 훅 내부에서 리액트의 훅(`useState`, `useEffect`, `useReducer` 등)을 사용할 수 있다.
    - **반환 값**: 커스텀 훅은 필요한 값을 반환할 수 있다. 객체나 배열 형태로 반환하여 필요한 값들을 제공할 수 있다.
    - 일반적으로 src 디렉터리에 hooks 라는 디렉터리를 만들어 그 안에 커스텀 훅 파일들을 저장한다.
- Context API

  - 컴포넌트 트리를 통해 전역적으로 값을 공유할 수 있게 해주는 기능
  - props drilling(여러 단계에 걸쳐 props를 전달하는 과정)을 피할 수 있다.
  - 사용법

    1. Context 생성

       - 먼저, `React.createContext()` 라는 함수를 사용하여 Context를 생성한다.

         ```jsx
         import React from "react";

         const UserContext = React.createContext(null);

         export default UserContext;
         ```

    2. Provider 생성

       - Provider는 Context 값을 제공하는 역할을 한다. Provider를 사용할 때는 `value` 라는 값을 설정해주면 된다.

         ```jsx
         import React, { useState } from "react";
         import UserContext from "./UserContext";

         const UserProvider = ({ children }) => {
           const [user, setUser] = useState({ name: "John Doe", age: 30 });

           return (
             <UserContext.Provider value={{ user, setUser }}>
               {children}
             </UserContext.Provider>
           );
         };

         export default UserProvider;
         ```

    3. Consumer 사용

       - Consumer를 사용하여 Context에서 제공된 값을 사용할 수 있다. Consumer는 함수형 컴포넌트와 클래스형 컴포넌트에서 모두 사용할 수 있다.

         ```jsx
         import React, { useContext } from "react";
         import UserContext from "./UserContext";

         const UserProfile = () => {
           const { user, setUser } = useContext(UserContext);

           const updateName = () => {
             setUser({ ...user, name: "Jane Doe" });
           };

           return (
             <div>
               <h1>User Profile</h1>
               <p>Name: {user.name}</p>
               <p>Age: {user.age}</p>
               <button onClick={updateName}>Change Name</button>
             </div>
           );
         };

         export default UserProfile;
         ```

    4. Provider로 감싸기

       - Provider를 루트 컴포넌트나 필요한 컴포넌트 트리에 감싸서 Context를 제공할 수 있다.
       - 이렇게 설정해주면 Provider에 의하여 감싸진 컴포넌트 중 어디서든 Context의 값을 바로 조회해서 사용할 수 있다.

         ```jsx
         import React from "react";
         import ReactDOM from "react-dom";
         import App from "./App";
         import UserProvider from "./UserProvider";

         ReactDOM.render(
           <UserProvider>
             <App />
           </UserProvider>,
           document.getElementById("root")
         );
         ```

- immer 라이브러리

  - 불변성(Immutability)을 유지하면서 상태를 쉽게 업데이트할 수 있도록 도와주는 JS 라이브러리
  - 리액트와 같이 상태 관리가 중요한 라이브러리와 함께 사용하면 매우 유용하다.
  - 사용법

    1. immer 설치

       ```bash
       npm install immer
       ```

    2. 코드의 상단에서 immer를 불러와 사용한다. 보통 `produce`라는 이름으로 불러온다.

       ```jsx
       import produce from "immer";
       ```

    3. `produce` 함수는 두 개의 인수를 받는다. 첫 번째 인수는 초기 상태이며, 두 번째 인수는 드래프트 상태를 변경하는 콜백 함수이다. 이 콜백 함수 내에서 드래프트 상태를 자유롭게 변경할 수 있다. 만약에 첫 번째 인수를 생략하고 바로 업데이트 함수를 넣어주면, 반환 값은 새로운 상태가 아닌 상태를 업데이트 해주는 함수가 된다.

       ```jsx
       import React, { useState } from "react";
       import produce from "immer";

       const App = () => {
         const [state, setState] = useState({
           user: { name: "John Doe", age: 30 },
           todos: [
             { id: 1, text: "Learn React", completed: false },
             { id: 2, text: "Learn Immer", completed: false },
           ],
         });

         const updateAge = () => {
           setState(
             produce((draft) => {
               draft.user.age += 1;
             })
           );
         };

         const toggleTodo = (id) => {
           setState(
             produce((draft) => {
               const todo = draft.todos.find((todo) => todo.id === id);
               if (todo) {
                 todo.completed = !todo.completed;
               }
             })
           );
         };

         return (
           <div>
             <h1>User: {state.user.name}</h1>
             <p>Age: {state.user.age}</p>
             <button onClick={updateAge}>Increase Age</button>
             <ul>
               {state.todos.map((todo) => (
                 <li key={todo.id}>
                   <label>
                     <input
                       type="checkbox"
                       checked={todo.completed}
                       onChange={() => toggleTodo(todo.id)}
                     />
                     {todo.text}
                   </label>
                 </li>
               ))}
             </ul>
           </div>
         );
       };

       export default App;
       ```
