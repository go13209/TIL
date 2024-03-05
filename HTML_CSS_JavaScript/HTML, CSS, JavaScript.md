# HTML, CSS, JavaScript

- HTML (Hyper Text Markup Language)

  - 웹 페이지의 의미와 구조를 정의하는 언어

- CSS (Cascading Style Sheet)

  - 웹 페이지의 디자인과 레이아웃을 구성하는 언어
  - CSS Selectors 종류
    - 기본 선택자
      - 전체(\*) 선택자
      - 요소(tag) 선택자
        - 지정한 모든 태그를 선택
      - 클래스(class) 선택
        - 주어진 클래스 속성을 가진 모든 요소를 선택
          **.index**는 class="index"를 가진 모든 요소를 선택
      - 아이디(id) 선택자
        - 주어진 아이디 속성을 가진 요소 선택
        - 문서에는 주어진 아이디를 가진 요소가 하나여야 함
          **#index**는 id="index"를 가진 요소를 선택
      - 속성(attribute) 선택자
    - 결합자(Combinators)
      - 자손 결합자(" "(space))
        - 첫 번째 요소의 자손 요소들 선택
          **p span**은 <P> 안에 있는 모든 <span>을 선택(하위 레벨 상관 없이)
      - 자식 결합자(>)
        - 첫 번째 요소의 직계 자식만 선택
          **ul > li**은 <ul> 안에 있는 모든 <li>를 선택(한 단계 아래 자식들만)
    - Cascade(계단식) & Specificity(우선순위)
      - Cascade(계단식)
        - 동일한 우선순위를 같은 규칙이 적용될 때 CSS에서 마지막에 나오는 규칙이 사용됨
      - Specificity(우선순위)
        - 선택자별로 정해진 우선순위 점수에 따라 점수가 높은 규칙이 사용됨
        - 우선순위 순서
          1. !important
          2. 우선순위
             - 인라인 스타일 > id 선택자 > class 선택자 > 요소 선택자
          3. 소스 코드 순
  - 상속
    - CSS는 상속을 통해 부모 요소의 속성을 자식에게 상속함
    - 코드의 재사용성을 높임
    - 상속되는 속성: Text 관련 요소(font, color, text-align), opacity, visibility 등
    - 상속되지 않는 속성: Box model 관련 요소(width, height, margin, padding, border, box-sizing, display), position 관련 요소(position, top/right/bottom/left, z-index) 등
  - Box Model
    - Block (상-하)
      - 항상 새로운 행으로 나뉨
      - width와 height 속성을 사용하여 너비와 높이를 지정 가능
      - 기본적으로 width 속성을 지정하지 않으면 박스의 너비는 사용 가능한 공간의 100%
      - 대표적인 block 타입 태그: h1~6, p, div
    - Inline (좌-우)
      - 새로운 행으로 나뉘지 않음
      - width와 height 속성을 사용할 수 없음
      - 수직 방향
        - padding, margins, borders가 적용되지만 다른 요소를 밀어낼 수는 없음
      - 수평 방향
        - padding, margins, borders가 적용되어 다른 요소를 밀어낼 수 있음
      - 대표적인 inline 타입 태그: a, img, span
    - display: inline-block
      - inline과 block 요소 사이의 중간 지점을 제공하는 display 값
      - 요소가 줄 바꿈 되는 것을 원하지 않으면서 너비와 높이를 적용하고 싶은 경우에 사용
      - block 요소의 특징을 가짐
        - 너비 및 높이 속성 적용 가능
        - 패딩, 여백 및 테두리로 인해 다른 요소가 상자에서 밀려남
    - Margin collapsing (마진 상쇄)
      - 두 block 타입 요소의 margin top과 bottom이 만나 결합하는 현상
      - 각 요소에 대한 상-하 margin을 각각 설정할 필요 없이 한 요소에만 설정하면 됨
  - CSS Position
    - Position 유형별 특징
      - static (기본값)
        - 요소를 Normal Flow에 따라 배치
      - relative
        - 요소를 Normal Flow에 따라 배치
        - 자기 자신이 기준
        - 요소가 차지하는 공간은 static일 때와 같음
      - absolute
        - 요소를 Normal Flow에서 제거
        - 가장 가까운 relative 부모 요소가 기준
        - 문서에서 요소가 차지하는 공간이 없어짐
      - fixed
        - 요소를 Normal Flow에서 제거
        - 현재 화면 영역(viewpoint)이 기준
        - 문서에서 요소가 차지하는 공간이 없어짐
      - sticky
        - 요소를 Normal Flow에 따라 배치
        - 가장 가까운 block 부모 요소가 기준
        - 요소가 특정 임계점에 도달했을 때 그 위치에 고정됨(fixed)
        - 만약 다음 sticky 요소가 나오면 다음 sticky 요소가 이전 sticky 요소의 자리를 대체
    - z-index
      - 요소가 겹쳤을 때 어떤 요소 순으로 위에 나타낼지 결정
      - 정숫값을 사용해 Z축 순서를 지정
      - 더 큰 값을 가진 요소가 작은 값의 요소를 덮음
  - CSS Flexbox
    - flex 레이아웃
      - flex-direction
        - flex item이 나열되는 방향을 지정
        - column으로 지정할 경우 주축이 변경됨
        - reverse로 지정하면 시작 선과 끝 선이 서로 바뀜
      - flex-wrap
        - flex item 목록이 flex container의 하나의 행에 들어가지 않을 때 다른 행에 배치할지 여부 설정
      - justify-content
        - 주축을 따라 flex item과 주위에 공간을 분배
      - align-content
        - 교차 축을 따라 flex item과 주위에 공간을 분배
        - flex-wrap이 wrap 또는 wrap-reverse로 설정된 여러 행에만 적용됨
        - 한 줄짜리 행에는 (flex-wrap이 nowrap으로 설정된 경우) 효과 없음
      - align-items
        - 교차 축을 따라 flex item 행을 정렬
      - align-self
        - 교차 축을 따라 개별 flex item을 정렬
      - flex-grow
        - flex item 요소에 flex container 요소 내부에서 할당 가능한 공간을 할당
        - 모든 flex item 요소가 동일한 값을 갖는다면 flex-container 내부에서 동일한 공간을 할당받음
        - 다른 값을 갖는다면 공간 값을 나누어 할당받음

- JavaScript

  - Basic syntax of JavaScript

    - 변수 선언 키워드
      - let
        - 재할당 가능 & 재선언 불가능
      - const (constant, 상수)
        - 항상 일정한 값
        - 재할당 불가능 & 재선언 불가능
        - 재할당의 경우 원시값은 불가능하지만 배열 내 값이나 객체 속성값은 변경 가능
      - var
        - 자바스크립트에서 이전에 변수를 선언하기 위해 사용했던 키워드로 여전히 유효함
        - 재할당 가능 & 재선언 가능
        - scope 범위가 전역/함수로 제한되어 블록 레벨 스코프가 없음
        - var를 사용한 변수는 undefined라는 초기화된 값과 함께 호이스팅됨
          > **호이스팅(hoisting) -** 변수의 선언과 함수의 선언이 각 스코프의 맨 위로 옮겨지는 것
        - **위의 이유로 var는 의도치 않은 오류를 발생시키고 디버깅을 어렵게 만들기 때문에 let과 const 키워드 사용을 권장함**
    - 데이터 타입

      - 원시 자료형

        - 변수에 값이 직접 저장되는 자료형(불변, 값이 복사)
        - Number: 정수 또는 숫자를 표현하는 자료형
        - NaN(Not A Number): 숫자가 아닌 값을 뜻하지만 숫자로 간주됨

          ```jsx
          > typeof 4;
          < "number"

          > typeof 4.21548;
          < "number"

          > 0/0;
          < NaN

          > NaN * 123;
          < NaN

          > typeof NaN;
          < "number"
          ```

        - String: 텍스트 데이터를 표현하는 자료형
          - 덧셈을 통해 문자열끼리 붙일 수 있음
          - 숫자와 문자열을 더할 경우 숫자를 문자열로 변환하여 합침
          - **'Template Literal'을 사용하여 문자열 사이에 변수 삽입 가능(따옴표가 아닌 백틱(backtick)을 사용)**
          ```jsx
          const age = 10;
          **const message = `홍길동은 ${age}세입니다.`;**
          console.log(message);
          ```
        - Boolean: true와 false
          - **조건문 또는 반복문에서 boolean이 아닌 데이터 타입은 '자동 형 변환 규칙'에 따라 true 또는 false로 변환됨**
        - null: 변수의 값이 없음을 의도적으로 표현할 때 사용
        - undefined: 정의되지 않은 값
          - 변수 선언 이후 직접 값을 할당하지 않으면 자동으로 할당됨

      - 참조 자료형
        - 객체의 주소가 저장되는 자료형(가변, 주소가 복사)
        - Objects(Object, Array, Function)
          - 배열(Array): 값의 순서 있는 집합
            - 대괄호([ ]) 사용
            - 인덱스를 사용해 특정 요소를 찾거나 새 값을 해당 칸에 넣을 수 있음

    - 연산자

      - 기본 수학 연산자
        - - : 더하기
        - - : 빼기
        - - : 곱하기
        - / : 나누기
        - % : 나머지
        - \*\* : 거듭제곱
      - 할당 연산자

        - 오른쪽에 있는 피연산자의 평가 결과를 왼쪽 피연산자에 할당하는 연산자
        - increment(++) : 피연산자의 값을 1 증가시키는 연산자
        - decrement(--) : 피연산자의 값을 1 감소시키는 연산자

          - i++ vs. ++i
            - i++ : 후위 증가 연산자
              - 먼저 변수의 현재 값을 반환한 다음 1 증가시킴
            - ++i : 전치 증가 연산자
              - 먼저 변수의 값을 1 증가시킨 다음, 증가한 값을 결과로 반환

          ```jsx
          > let i = 5;
          < undefined

          > let result = i++;
          < undefined

          > result;
          < 5

          > i;
          < 6
          ```

          ```jsx
          > let i = 5;
          < undefined

          > let result = ++i;
          < undefined

          > result;
          < 6

          > i;
          < 6
          ```

          - **+= 또는 -=와 같이 더 분명한 표현으로 적는 것을 권장함**

      - 비교 연산자
        - 피연산자들(숫자, 문자, Boolean 등)을 비교하고 결괏값을 boolean으로 반환하는 연산자
        - \> , <, ≥, ≤
      - 동등 연산자(==)

        - 두 피연산자가 같은 값으로 평가되는지 비교 후 boolean 값을 반환
        - 비교할 때 암묵적 타입 변환을 통해 타입을 일치시킨 후 같은 값인지 비교
        - 두 피연산자가 모두 객체일 경우 메모리의 같은 객체를 바라보는지 판별
        - 예상치 못한 결과가 발생할 수 있으므로 **특별한 경우를 제외하고 사용하지 않음**

        ```jsx
        > 0 == false;
        < true

        > null == undefined;
        < true

        > 1 == '1';
        < true

        > 1 != '1';
        < false
        ```

      - 일치 연산자(===)

        - 두 피연산자의 값과 타입이 모두 같은 경우 true를 반환
        - 같은 객체를 가리키거나, 같은 타입이면서 같은 값인지를 비교
        - 엄격한 비교가 이뤄지며 암묵적 타입 변환이 발생하지 않음

        ```jsx
        > 0 === false;
        < false

        > null === undefined;
        < false

        > 1 === '1';
        < false

        > 1 !== '1';
        < true
        ```

      - 논리 연산자
        - and 연산은 '&&' 연산자
          - 모든 조건이 참이어야만 참, 어느 한 조건이라도 거짓이면 거짓
        - or 연산은 '||' 연산자
          - 어느 한 조건이라도 참이면 참, 모든 조건이 거짓이면 거짓
        - not 연산은 '!' 연산자
          - 값을 반전시킴
          - 거짓은 참으로, 참은 거짓으로 바꿈

    - 조건문

      - if

        - 조건 표현식의 결괏값을 boolean 타입으로 변환 후 참/거짓을 판단

        ```jsx
        const name = "manager";

        if (name === "admin") {
          console.log("관리자님 환영합니다.");
        } else if (name === "manager") {
          console.log("매니저님 환영합니다.");
        } else {
          console.log(`${name}님 환영합니다.`);
        }
        ```

      - switch

        - 특정 변수를 다양한 상황(케이스)와 비교하여 조건에 따라 다른 동작을 수행
        - break는 switch 조건문을 멈추는 역할
          - break가 없다면 조건과 일치하는 case의 동작 부분을 수행한 뒤 그 다음 동작도 수행하게 되므로 case별로 동작을 구분하고 싶다면 break문을 작성해야 한다.
        - default문은 if 조건문의 ‘else’와 같은 역할

        ```jsx
        const number = 10;

        switch (number) {
        	case 1:
        		console.log(number);
        		**break;**
        	case 10:
        		console.log(number);
        		**break;**
        	**default:**
        		console.log('해당하는 조건이 없습니다');
        }
        ```

    - 반복문

      - while

        - 테스트 조건이 거짓이 될 때까지 지정된 구문을 계속해서 수행

        ```jsx
        while (조건문) {
          // do something
        }
        ```

        ```jsx
        let i = 0;

        while (i < 6) {
          console.log(i);
          i += 1;
        }
        ```

      - do…while

        - while문과 동일
        - 단, 구문이 실행된 뒤에 테스트 조건이 평가되므로 구문은 무조건 한 번은 실행됨

        ```jsx
        let i = 0;

        do {
          console.log(i);
          i += 1;
        } while (i < 6);
        ```

      - for
        - 특정한 조건이 거짓으로 판별될 때까지 반복
        ```jsx
        for ([초기문]; [조건문]; [증감문];) {
        // do something
        }
        ```
        ```jsx
        for (let i = 0; i < 6; i++;) {
          console.log(i);
        }
        ```
      - for...in

        - 객체(object)의 속성을 순회할 때 사용
        - 객체의 속성에 대해 반복

        ```jsx
        for (variable in object) {
          statements;
        }
        ```

        ```jsx
        const fruits = { a: "apple", b: "banana" };

        for (const key in fruits) {
          console.log(key);
        }
        ```

      - for...of

        - 반복 가능한 객체(배열, 문자열 등)를 순회할 때 사용
        - 객체의 요소에 대한 반복

        ```jsx
        for (variable of iterable) {
          statements;
        }
        ```

        ```jsx
        const numbers = [0, 1, 2, 3];

        for (const number of numbers) {
          console.log(number);
        }
        ```

  - Method

    - 객체 속성에 정의된 함수
    - **‘this’ 키워드를 사용해 객체에 대한 특정한 작업을 수행할 수 있음**
    - 문자열 메소드
      - toUpperCase() : 문자열을 대문자로 변환해 반환
      - toLowerCase() : 문자열을 소문자로 변환해 반환
      - trim() : 원본 문자열을 수정하지 않고, 문자열 양 끝의 공백을 제거한 새로운 문자열을 반환
        - trimStart() : 문자열 시작 부분의 공백을 제거
        - trimEnd() : 문자열 끝 부분의 공백을 제거
      - repeat(count) : 주어진 횟수만큼 반복해 붙인 새로운 문자열을 반환
      - padStart(length[, str]) : 현재 문자열의 시작을 다른 문자열로 채워 주어진 길이를 만족하는 새로운 문자열을 반환
      - padEnd(length[, str]) : 현재 문자열의 끝을 다른 문자열로 채워 주어진 길이를 만족하는 새로운 문자열을 반환
      - indexOf(value[, index]) : (주어진 인덱스 위치에서부터 찾기 시작하여) 주어진 값과 일치하는 첫 번째 인덱스를 반환하며 일치하는 값이 없으면 -1을 반환
      - includes(str[, index]) : (주어진 인덱스 위치에서부터 찾기 시작하여) 주어진 문자열이 원본 문자열에 포함되어 있는지를 판별하고, 결과를 true 또는 false 로 반환하며 검색 시 대소문자를 구분
      - startsWith(str[, index]) : (주어진 인덱스 위치에서부터) 원본 문자열이 특정 문자로 시작하는지 확인하여 결과를 true 혹은 false로 반환
      - endsWith(str[, length]) : (찾고자 하는 문자열의 길이값 범위 내에서) 원본 문자열이 특정 문자로 끝나는지 확인하여 결과를 true 혹은 false로 반환
      - replace(str, NewStr) : 주어진 문자열을 교체 문자열로 바꾸어 새로운 문자열을 반환하며 첫 번째 문자열만 변경
      - replaceAll(str, NewStr) : 주어진 문자열과 일치하는 모든 부분을 교체 문자열로 바꾸어 새로운 문자열을 반환
      - substring(indexStart[, indexEnd]) : 원본 문자열의 시작 인덱스부터 종료 인덱스 전까지 문자열의 부분 문자열을 반환
      - split(seperator) : 원본 문자열을 지정한 구분자를 이용하여 여러 개의 문자열로 나누어 반환
      - slice(indexStart[, indexEnd]) : 원본 문자열의 시작 인덱스부터 종료 인덱스 전까지 문자열의 일부를 추출하여 새로운 문자열을 반환
    - 배열 메소드

      - push(element1[, ...[, elementN]]) : 배열의 끝에 하나 이상의 요소를 추가
      - pop() : 배열에서 마지막 요소를 제거하고 그 요소를 반환
      - unshift([...elementN]) : 새로운 요소를 배열의 맨 앞쪽에 추가
      - shift() : 배열에서 첫 번째 요소를 제거하고 제거된 요소를 반환
      - concat([value1[, value2[, ...[, valueN]]]]) : 인자로 주어진 배열이나 값들을 기존 배열에 합쳐서 새 배열을 반환
      - includes(str[, index]) : (주어진 인덱스 위치에서부터 찾기 시작하여) 배열이 특정 요소를 포함하고 있는지를 판별하고, 결과를 true 또는 false 로 반환하며 검색 시 대소문자를 구분
      - indexOf(element[, index]) : (주어진 인덱스 위치에서부터 찾기 시작하여) 주어진 요소와 일치하는 첫 번째 인덱스를 반환하며 일치하는 값이 없으면 -1을 반환
      - join([separator]) : 배열의 모든 요소를 연결해 하나의 문자열로 만듦
      - reverse() : 주어진 배열의 순서를 뒤집어 원본 배열을 변형하여 그 결과값을 반환
      - slice([begin[, end]]) : 어떤 배열의 begin 부터 end 이전까지에 대한 복사본을 새로운 배열 객체로 반환하며 원본 배열은 바뀌지 않음
      - splice(start[, deleteCount[, item1[, item2[, ...]]]]) : 배열의 기존 요소를 삭제 또는 교체하거나 새 요소를 추가하여 배열의 내용을 변경

        ```jsx
        const months = ["Jan", "March", "April", "June"];
        months.splice(1, 0, "Feb");
        // Inserts at index 1
        console.log(months);
        // Array ["Jan", "Feb", "March", "April", "June"]

        months.splice(4, 1, "May");
        // Replaces 1 element at index 4
        console.log(months);
        // Array ["Jan", "Feb", "March", "April", "May"]
        ```

      - fill(value[, start[, end]]) : 배열의 (지정한) 시작 인덱스부터 (지정한) 끝 인덱스의 이전까지 정적인 값 하나로 채움
      - forEach() : 주어진 함수를 배열 요소 각각에 대해 실행

        ```jsx
        arr.forEach(callback(currentvalue[, index[, array]])[, thisArg])
        ```

        - callback : 각 요소에 대해 실행할 함수
          - currentValue : 처리할 현재 요소
          - index : 처리할 현재 요소의 인덱스
          - array : forEach()를 호출한 배열
        - thisArg : callback을 실행할 때 this로 사용할 값

        ```jsx
        const arraySparse = [1, 3, , 7];
        let numCallbackRuns = 0;

        arraySparse.forEach(function (element) {
          console.log(element);
          numCallbackRuns++;
        });

        console.log("numCallbackRuns: ", numCallbackRuns);

        // 1
        // 3
        // 7
        // numCallbackRuns: 3
        ```

      - map() : 배열 내의 모든 요소 각각에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환

        ```jsx
        arr.map(callback(currentValue[, index[, array]])[, thisArg])
        ```

        - callback : 새로운 배열 요소를 생성하는 함수
          - currentValue : 처리할 현재 요소
          - index : 처리할 현재 요소의 인덱스
          - array : map()을 호출한 배열
        - thisArg : callback을 실행할 때 this로 사용되는 값

        ```jsx
        const numbers = [1, 4, 9];
        const doubles = numbers.map(function (num) {
          return num * 2;
        });

        // doubles는 [2, 8, 18]
        // numbers는 [1, 4, 9]
        ```

      - find(callback[, thisArg]) : 주어진 판별 함수를 만족하는 첫 번째 요소의 값을 반환하며 그런 요소가 없다면 undefined를 반환
      - findIndex(callback(element[, index[, array]])[, thisArg]) : 주어진 판별 함수를 만족하는 배열의 첫 번째 요소에 대한 인덱스를 반환하며 만족하는 요소가 없으면 -1을 반환
      - filter(callback(element[, index[, array]])[, thisArg]) : 주어진 함수의 테스트를 통과하는 모든 요소를 모아 새로운 배열로 반환
      - reduce(callback[, initialValue]) : 배열의 각 요소에 대해 주어진 리듀서 (reducer) 함수를 실행하고, 하나의 결과값을 반환

        ```jsx
        const array1 = [1, 2, 3, 4];

        // 0 + 1 + 2 + 3 + 4
        const initialValue = 0;
        const sumWithInitial = array1.reduce(
          (accumulator, currentValue) => accumulator + currentValue,
          initialValue
        );

        console.log(sumWithInitial);
        // 10
        ```

  - Math Object

    - 자바스크립트에 내장된 Math 객체
    - 수학과 관련된 프로퍼티와 메서드 제공
    - Math.floor(x) : 소수점 이하를 버림
    - Math.ceil(x) : 소수점 이하를 무조건 올림
    - Math.round(x) : 소수점 이하를 반올림
    - Math.random() : 0 이상 1 미만의 소수점 숫자를 임의 생성

      ```jsx
      // 1부터 10 사이의 임의의 자연수 생성하는 법
      Math.floor(Math.random() * 10) + 1;

      // 20부터 22 사이의 임의의 자연수 생성하는 법
      Math.floor(Math.random() * 3) + 20;
      ```

    - Math.abs(x) : 주어진 숫자의 절대값 반환
    - Math.pow(x, y) : x를 y 값으로 거듭제곱한 수 반환

  - Object

    - 키(key)와 값(value)로 구성된 속성(property)들의 집합
    - 객체 축약 표현

      ```jsx
      const name = "홍길동";
      const country = "Korea";

      const user = {
        name,
        country,
      };

      console.log(user);
      // {name: '홍길동', country: 'Korea'}
      ```

    - 메소드 축약 표현

      ```jsx
      const obj = {
        greeting() {
          console.log("Hi!");
        },
      };

      obj.greeting();
      // Hi!
      ```

    - Object.keys(obj) : 주어진 객체의 속성 이름들로 이루어진 배열을 반환
    - Object.values(obj) : 주어진 객체의 속성 값들로 이루어진 배열을 반환
    - Object.entries(obj) : 주어진 객체의 모든 프로퍼티를 [key, value] 쌍의 배열 형태로 반환
      - 정적 메소드는 생성된 객체에 내장되어 있는 것이 아니라 Object, Array 클래스가 가지고 있기 때문에 앞에 Object 또는 Array 등을 붙여야 사용 가능

  - DOM 선택 및 조작
    > **DOM (Document Object Model, 문서 객체 모델) -** XML이나 HTML 문서에 접근하기 위한 인터페이스로, 문서 내의 모든 요소를 정의하고, 각각의 요소에 접근하는 방법을 제공
    - 자바스크립트는 DOM을 조작할 수 있는 프로그래밍 언어 중 하나
      >
    - document.querySelector(selector)
      - 제공한 선택자와 일치하는 element 한 개 선택
      - 제공한 CSS selector를 만족하는 첫 번째 element 객체를 반환(없다면 null 반환)
    - document.querySelectorAll(selector)
      - 제공한 선택자와 일치하는 여러 element를 선택
      - 매칭할 하나 이상의 셀렉터를 포함하는 유효한 CSS selector를 인자(문자열)로 받음
      - 제공한 CSS selector를 만족하는 NodeList를 반환
    - 속성(attribute) 조작
      - 클래스 속성 조작
        - element.classList
          - 요소의 클래스 목록을 DOMTokenList(유사 배열) 형태로 반환
        - element.classList.add()
          - 지정한 클래스 값을 추가
        - element.classList.remove()
          - 지정한 클래스 값을 제거
      - 일반 속성 조작
        - element.getAttribute()
          - 해당 요소에 지정된 값을 반환
        - element.setAttribute()
          - 지정된 요소의 속성값을 설정
          - 속성이 이미 있으면 값이 업데이트 / 그렇지 않으면 지정된 이름과 값으로 새 속성이 추가
        - element.removeAttribute()
          - 요소에서 지정된 이름을 가진 속성 제거
    - HTML 콘텐츠 조작
      - element.textContent
        - 요소의 텍스트 콘텐츠를 표현
    - DOM 조작
      - document.createElement()
        - 지정한 이름의 HTML 요소를 만들어 반환
      - element.appendChild()
        - 지정한 요소에 자식 노드를 생성
      - element.removeChild()
        - 지정한 요소에서 지정한 자식 노드를 제거
    - style 조작
      - element.style.property
        - element 스타일 속성값을 변경
        - 예시: element.style.backgroundColor = "red";
  - Functions

    - 모든 JavaScript 함수는 Function 객체

    ```jsx
    function name (**[param[, param2[, ...paramN]]]**) {
    	statements
    	return value
    }
    ```

    - 인자
      - 함수의 입력 값 = 인자 = Argument
    - 매개변수

      - param, param2, ... paramN
      - 함수의 입력 변수 = 매개변수 = Parameter
      - 매개변수와 인자의 개수가 불일치하는 경우

        - 매개변수 > 인자

          - 기본 함수 매개변수(default function parameter) 사용

          ```jsx
          function sum(a, b = 0) {
            console.log(a + b);
          }

          sum(10); //10
          sum(10, 20); //30
          ```

        - 매개변수 < 인자

          - 나머지 매개변수(rest parameter) 사용

          ```jsx
          function print(a, b, ...rest) {
            console.log(a);
            console.log(b);
            console.log(rest);
          }

          sum(10, 20, 30, 40, 50);
          //10
          //20
          //[30, 40, 50]
          ```

    - 함수 표현식과 화살표 함수 표현식

      - 함수 표현식
        - 익명 함수 사용 가능
        - 호이스팅 없음(사용 권장)
          > **호이스팅이란? -** 인터프리터가 변수와 함수의 메모리 공간을 선언 전에 미리 할당하는 것
        - 변수를 정의하는 코드보다 사용하는 코드가 앞서 등장할 수 있다.
          >
        ```jsx
        const funcName = function () {
          statements;
        };
        ```
      - 화살표 함수 표현식

        - 함수 표현식의 간결한 표현법
          - function 키워드 제거 후 매개변수와 중괄포 사이에 화살표(⇒) 작성
          - 함수의 매개변수가 하나 뿐이라면 매개변수의 () 생략 가능
            - 인수가 하나도 없을 땐 빈 괄호 또는 \_로 표시할 수 있다. 단, 이 때 괄호는 생략할 수 없다.
          - 함수 본문의 표현식이 한 줄이라면 {}와 return 생략 가능
            - 본문이 여러 줄로 구성되었다면 중괄호를 사용해야 한다. 단, 이 경우는 반드시 `return` 지시자를 사용해 반환 값을 명기해 주어야 한다.

        ```jsx
        function hello() {
          console.log("Hello!");
          console.log("World!");
        }

        hello();
        ```

        ```jsx
        const hello = () => {
          console.log("Hello!");
          console.log("World!");
        };

        hello();
        ```

        ```jsx
        function sum(a, b) {
          return a + b;
        }

        console.log(sum(10, 20));
        ```

        ```jsx
        const sum = (a, b) => a + b;

        console.log(sum(10, 20));
        ```

        ```jsx
        function greeting(user) {
          console.log(`Hello, ${user}!`);
        }

        greeting("홍길동");
        ```

        ```jsx
        const greeting = (user) => console.log(`Hello, ${user}!`);

        greeting("홍길동");
        ```

  - Event

    - 어떤 동작이나 상태 등의 사건이 발생하는 것 (예: 사용자가 키보드를 누르거나 마우스를 클릭하는 등의 사건)
    - 특정 이벤트를 감지하는 Event Listener를 사용해서 Event Handler를 지정하여 이벤트에 대한 반응(동작)을 처리
    - .addEventListener(event type, handler)

      - 특정 이벤트가 발생하면 특정 함수 실행

      ```jsx
      // 버튼 클릭시 숫자가 1씩 증가
      <body>
      	<button id='btn'>버튼</button>
      	<p id='counter'>0</p>
      	<script>
      		let counterNumber = 0
      		const btn = document.querySelector(#btn)

      		btn.addEventListener('click', () => {
      			counterNumber += 1
      			const pTag = document.querySelector('#counter')
      			pTag.textContent = counterNumber
      		})
      	</script>
      </body>
      ```

    - .removeEventListener(event type, handler) : 특정 이벤트가 발생하면 등록된 이벤트 리스너를 삭제
    - .preventDefault() : 현재 이벤트의 기본 동작을 중단
