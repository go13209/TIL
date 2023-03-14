# ⭐ Web - JavaScript

## 💡 History of JavaScript

- 웹 브라우저의 상용화
  - 1994년, Netscape 사의 최초 상용 웹 브라우저인 Netscape Navigator 출시
  - 당시 약 90%의 시장 점유율을 차지
- 웹 브라우저 경쟁
  - 1995년 Microsoft의 Internet Explorer(IE) 출시
  - Netscape는 IE와 경쟁할 차기 웹 브라우저 개발에 착수
  - 당시에는 웹 페이지에 동적인 기능이 없었기 때문에 Netscape는 웹 페이지의 동적인 기능을 제공하기 위한 새로운 언어를 개발하기 시작
- JavaScript의 탄생
  - 당시 Netscape 소속 개발자 Brandon Eich가 JavaScript를 개발
  - JavaScript는 Netscape Navigator 2.0에 탑재되어 큰 인기를 누림
- JavaScript의 파편화
  - Microsoft는 JavaScript의 파생 버전인 Jscript를 IE 3.0에 채택
  - 이 과정에서 Netscape와 Microsoft 외의 많은 회사가 자체적으로 JavaScript를 탑재해 독자적으로 업데이트함
  - 이에 따라 같은 코드가 브라우저마다 다르게 동작하는 등의 문제 발생(Cross Browsing 이슈 발생)
    - 추후 JavaScript 표준화의 배경이 됨
- 1차 브라우저 전쟁
  - Microsoft는 IE를 자사 윈도우 운영체제에 내장하여 무료로 배포
  - 빌 게이츠를 필두로 한 Microsoft의 공격적인 마케팅, 자금력, 막강한 윈도우 운영체제 점유율 앞에 Netscape는 빠르게 몰락하기 시작
  - 결국 IE의 시장 점유율은 2002년 약 96%에 달하며 Microsoft의 승리로 종료
  - 추후 Brandon Eich와 함께 Netscape에서 나온 핵심 개발진은 모질라 재단을 설립하여 Firefox 브라우저를 출시(2003)
- 2차 브라우저 전쟁
  - 2008년 구글에서 Chrome 브라우저를 출시
  - 출시 3년 만에 10년간 쌓아온 Firefox의 점유율을 넘어섰고 그로부터 반년 뒤 IE의 점유율을 넘어섬
  - 빠른 속도, 압도적인 성능, 엄격한 웹 표준 준수, 강력한 개발자 도구를 제공
  - 웹 표준의 발전과 웹 애플리케이션의 대중화에 큰 역할을 하게 됨
- JavaScript 현황
  - 현재는 Chrome, Firefox, Safari, Microsoft Edge 등 다양한 웹 브라우저가 출시되어 있으며, 웹 브라우저 시장이 다양화되어 있음
  - 기존의 JavaScript는 브라우저에서만 웹 페이지의 동적인 기능을 구현하는 데 사용되었으나 이후 브라우저에서 벗어나 Node.js와 같은 서버 사이드 분야뿐만 아니라 다양한 프레임워크와 라이브러리들이 개발되면서 웹 개발 분야에서는 필수적인 언어로 자리 잡게 됨

## 💡 JavaScript의 표준화

- JavaScript의 파편화를 막기 위해 1997년 ECMA에서 ECMAScript라는 표준 언어를 정의
- 이후 ECMAScript는 독자적으로 발전하며 JavaScript보다 더 많은 기능을 제공하게 됨
- 2009년에는 ECMAScript 5(ES5)에서 안정성과 생산성을 크게 높임
- 2015년에는 ECMAScript 2015(ES6)에서 객체지향 프로그래밍 언어로써 많은 발전을 이루어 역사상 가장 중요한 버전으로 평가됨
- JavaScript는 ECMAScript의 구현 언어 중 하나

## 💡 DOM(Document Oject Model, 문서 객체 모델)

- 웹 페이지(Document)를 구조화된 객체로 제공하며 프로그래밍 언어가 웹페이지를 사용할 수 있게 연결함
- 문서(Document)는 웹 브라우저를 통해 해석되어 화면에 나타나며 DOM은 이러한 문서를 조작하는 방법을 제공하는 API
- 브라우저는 HTML 문서를 해석하여 DOM tree라는 객체의 트리로 구조화함
- DOM에서 모든 요소, 속성, 텍스트는 하나의 객체이며 모두 document 객체의 자식

## 💡 DOM Query(선택)

- 웹 페이지를 조작(생성, 추가, 삭제)하기 위해서는 먼저 조작하고자 하는 요소를 선택 또는 탐색하고 선택한 요소의 콘텐츠 또는 속성을 조작함
- document.querySelector(selector)
  - 제공한 선택자와 일치하는 element 한 개 선택
  - 제공한 CSS selector를 만족하는 첫 번째 element 객체를 반환(없다면 null 반환)
- document.querySelectorAll(selector)
  - 제공한 선택자와 일치하는 여러 element를 선택
  - 매칭할 하나 이상의 셀렉터를 포함하는 유효한 CSS selector를 인자(문자열)로 받음
  - 제공한 CSS selector를 만족하는 NodeList를 반환

## 💡 DOM Manipulation(조작)

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

## 💡 Basic syntax of JavaScript
- 변수 선언 키워드
  - let
    - `블록 스코프`를 갖는 지역 변수를 선언
    - 재할당 가능 & 재선언 불가능
    > 블록 스코프(Block Scope)
    >  - if, for, 함수 등의 **중괄호({}) 내부**를 가리킴
    >  - 블록 스코프를 가지는 변수는 블록 바깥에서 접근 불가능
  - const
    - 블록 스코프를 갖는 지역 변수를 선언
    - 재할당 불가능 & 재선언 불가능
- 데이터 타입
  - 원시 자료형
    - 변수에 값이 직접 저장되는 자료형(불변, 값이 복사)
    - Number: 정수 또는 숫자를 표현하는 자료형
    - String: 텍스트 데이터를 표현하는 자료형
      - 덧셈을 통해 문자열끼리 붙일 수 있음
      - **'Template Literal'을 사용하여 문자열 사이에 변수 삽입 가능(따옴표가 아닌 backtick을 사용)**
      ```js
      const age = 10
      const message = `홍길동은 ${age}세입니다.`
      console.log(message)
      ```
    - Boolean: true와 false
      - **조건문 또는 반복문에서 boolean이 아닌 데이터 타입은 '자동 형 변환 규칙'에 따라 true 또는 false로 변환됨**

      |데이터 타입|false|true|
      |----------|:------:|:----:|
      |undefined|항상 false|X|
      |null|항상 false|X|
      |Number|0, -0, NaN|나머지 모든 경우|
      |String|빈 문자열|나머지 모든 경우|

    - null: 변수의 값이 없음을 의도적으로 표현할 때 사용
    - undefined: 변수 선언 이후 직접 값을 할당하지 않으면 자동으로 할당됨
  - 참조 자료형
    - 객체의 주소가 저장되는 자료형(가변, 주소가 복사)
    - Objects(Object, Array, Function)
- 연산자
  - 할당 연산자
    - 오른쪽에 있는 피연산자의 평가 결과를 왼쪽 피연산자에 할당하는 연산자
    - 다양한 연산에 대한 단축 연산자 지원
    - increment(++)
      - 피연산자의 값을 1 증가시키는 연산자
    - decrement(--)
      - 피연산자의 값을 1 감소시키는 연산자
    - += 또는 -=와 같이 더 분명한 표현으로 적는 것을 권장함
  - 비교 연산자
    - 피연산자들(숫자, 문자, Boolean 등)을 비교하고 결과값을 boolean으로 반환하는 연산자
  - 동등 연산자(==)
    - 두 피연산자가 같은 값으로 평가되는지 비교 후 boolean 값을 반환
    - 비교할 때 암묵적 타입 변환을 통해 타입을 일치시킨 후 같은 값인지 비교
    - 두 피연산자가 모두 객체일 경우 메모리의 같은 객체를 바라보는지 판별
    - 예상치 못한 결과가 발생할 수 있으므로 **특별한 경우를 제외하고 사용하지 않음**
  - 일치 연산자(===)
    - 두 피연산자의 값과 타입이 모두 같은 경우 true를 반환
    - 같은 객체를 가리키거나, 같은 타입이면서 같은 값인지를 비교
    - 엄격한 비교가 이뤄지며 암묵적 타입 변환이 발생하지 않음
  - 논리 연산자
    - and 연산은 '&&' 연산자
    - or 연산은 '||' 연산자
    - not 연산은 '!' 연산자
- 조건문
  - if
    - 조건 표현식의 결과값을 boolean 타입으로 변환 후 참/거짓을 판단
    ```js
    const name = 'manager'

    if (name === 'admin') {
      console.log('관리자님 환영합니다.')
    } else if (name === 'manager') {
      console.log('매니저님 환영합니다.')
    } else {
      console.log(`${name}님 환영합니다.`)
    }
    ```
- 반복문
  - while
    - 조건문이 참이기만 문장을 계속해서 수행
    ```js
    while (조건문) {
      // do something
    }
    ```
    ```js
    let i = 0

    while (i < 6) {
      console.log(i)
      i += 1
    }
    ```
  - for
    - 특정한 조건이 거짓으로 판별될 때까지 반복
    ```js
    for ([초기문]; [조건문]; [증감문];) {
      // do something
    }
    ```
    ```js
    for (let i = 0; i < 6; i++) {
      console.log(i)
    }
    ```
  - for...in
    - 객체(object)의 속성을 순회할 때 사용
    - 객체의 속성에 대해 반복
    ```js
    for (variable in object) {
      statements
    }
    ```
    ```js
    const fruits = { a: 'apple', b: 'banana' }

    for (const key in fruits) {
      console.log(key) // a, b
      console.log(fruits[key]) // apple, banana
    }
    ```

  - for...of
    - 반복 가능한 객체(배열, 문자열 등)를 순회할 때 사용
    - 객체의 요소에 대한 반복
    ```js
    for (variable of iterable) {
      statements
    }
    ```
    ```js
    const numbers = [0, 1, 2, 3]

    for (const number of numbers) {
      console.log(number) // 0, 1, 2, 3
    }
    ```