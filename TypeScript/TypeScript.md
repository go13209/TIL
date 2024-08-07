# TypeScript

- 타입스크립트란?
  - TypeScript는 JS의 구문이 허용되는, JavaScript의 *상위 집합* 언어
  - 자바스크립트에 타입(type)을 추가한 언어
  - 타입스크립트의 등장 배경
    - JavaScript는 웹 페이지에 사소한 상호작용을 추가하기 위한 작은 스크립팅 언어로 시작하여, 규모에 상관없이 프론트엔드와 백엔드 애플리케이션에서 선택 가능한 언어로 성장했다. JavaScript로 작성된 프로그램의 크기, 범위 및 복잡성은 기하급수적으로 커졌지만, 다른 코드 단위 간의 관계를 표현하는 JavaScript 언어의 능력은 그렇지 못했다.
    - 이런 JavaScript의 문제점을 극복하기 위해서 타입 시스템을 추가하여 코드의 안정성과 유지보수성을 높인 TypeScript가 등장했다.
- 기본 타입

  - 숫자(number)
    - 부동 소수점 값
    - 16진수, 10진수 리터럴 및 2진수, 8진수 리터럴도 지원한다.
    ```tsx
    let age: number = 25;
    let pi: number = 3.14;
    ```
  - 문자열(string)
    - 텍스트 데이터 타입
    - 큰따옴표 (`"`)나 작은따옴표 (`'`)를 문자열 데이터를 감싸는데 사용한다.
    - 백틱/백쿼트 (<code>\`</code>) 문자로 감싸지며, `${ expr }`과 같은 형태로 표현식을 포함할 수 있다.
    ```tsx
    let name: string = "John";
    let greeting: string = `Hello, ${name}`;
    ```
  - 불리언(boolean)
    - 참/거짓(true/false) 값
    ```tsx
    let isStudent: boolean = true;
    let isGraduated: boolean = false;
    ```
  - 배열(Array)
    - 동일한 타입의 요소들을 모아 놓은 데이터 구조
    ```tsx
    let list: number[] = [1, 2, 3];
    let list: Array<string> = ["Alice", "Bob", "Charlie"];
    ```
  - 튜플(tuple)
    - 요소의 타입과 개수가 고정된 배열
    - 서로 다른 타입의 요소들을 가질 수 있다.
    ```tsx
    let person: [string, number] = ["Alice", 25];
    ```
  - 열거(enum)

    - 이름이 있는 상수들의 집합을 정의한다.

    ```tsx
    enum Direction {
      Up = 1,
      Down,
      Left,
      Right,
    }

    let d: Direction = Direction.Left; // 3
    ```

    - 위 코드에서 `Up`이 `1`로 초기화된 숫자 열거형을 선언했다. 그 지점부터 뒤따르는 멤버들은 자동으로 1 증가한 값을 갖는다. 즉, `Direction.Up`은 `1`, `Down`은 `2`, `Left`는 `3`, `Right`은 `4`를 값으로 가진다.

  - Any

    - 모든 타입의 값을 가질 수 있는 타입
    - 알지 못하는 타입을 표현해야 할 때 유용하다.

    ```tsx
    let list: any[] = [1, true, "free"];

    list[1] = 100;
    ```

  - void
    - 일반적으로 함수에서 반환 값이 없음을 나타낸다.
    ```tsx
    function sayHello(): void {
      console.log("Hello");
    }
    ```
    - `void`를 타입 변수에는 `null`(`--strictNullChecks`을 사용하지 않을 때만 해당)또는 `undefined` 만 할당할 수 있다.
  - null / undefined
    - 각각 null과 undefined 값만 가질 수 있다.
    ```tsx
    let u: undefined = undefined;
    let n: null = null;
    ```
    - 기본적으로 `null`과 `undefined`는 다른 모든 타입의 하위 타입이다. 이건, null과 undefined를 `number` 같은 타입에 할당할 수 있다는 것을 의미한다. 하지만, `--strictNullChecks`를 사용하면, `null`과 `undefined`는 오직 `any`와 각자 자신들 타입에만 할당 가능하다.
  - never
    - 절대 발생하지 않는 값의 타입
    - 보통 오류를 던지거나 무한 루프에 사용된다.
    ```tsx
    function error(message: string): never {
      throw new Error(message);
    }
    ```
  - 객체(object)

    - 원시 타입이 아닌 타입
    - `number`, `string`, `boolean`, `bigint`, `symbol`, `null`, `undefined`가 아닌 나머지

    ```tsx
    let person: { name: string; age: number } = {
      name: "Alice",
      age: 25,
    };
    ```

    - 프로퍼티의 이름 뒤에 ? 를 붙여주면 해당 프로퍼티를 선택적 프로퍼티로 만들어준다.

    ```tsx
    let user: {
      id?: number; // 선택적 프로퍼티가 된 id
      name: string;
    } = {
      id: 1,
      name: "Alice",
    };

    user = {
      name: "Joy",
    };
    ```

- 리터럴 타입
  - 하나의 값만 포함하도록 값 자체로 만들어진 타입
  ```tsx
  let strA: "hello" = "hello";
  let numA: 10 = 10;
  ```
