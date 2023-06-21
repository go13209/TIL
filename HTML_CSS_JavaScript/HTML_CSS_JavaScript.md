# HTML, CSS, JavaScript

- HTML (Hyper Text Markup Language)
    - 웹 페이지의 의미와 구조를 정의하는 언어

- CSS (Cascading Style Sheet)
    - 웹 페이지의 디자인과 레이아웃을 구성하는 언어
    - CSS Selectors 종류
        - 기본 선택자
            - 전체(*) 선택자
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
    - DOM 선택 및 조작
        
        > **DOM (Document Object Model, 문서 객체 모델)
        -** XML이나 HTML 문서에 접근하기 위한 인터페이스로, 문서 내의 모든 요소를 정의하고, 각각의 요소에 접근하는 방법을 제공
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
    - Basic syntax of JavaScript
        - 변수 선언 키워드
            - let
                - 재할당 가능 & 재선언 불가능
            - const
                - 재할당 불가능 & 재선언 불가능
        - 데이터 타입
            - 원시 자료형
                - 변수에 값이 직접 저장되는 자료형(불변, 값이 복사)
                - Number: 정수 또는 숫자를 표현하는 자료형
                - String: 텍스트 데이터를 표현하는 자료형
                    - 덧셈을 통해 문자열끼리 붙일 수 있음
                    - **'Template Literal'을 사용하여 문자열 사이에 변수 삽입 가능(따옴표가 아닌 backtick을 사용)**
                    
                    ```jsx
                    const age = 10;
                    const message = `홍길동은 ${age}세입니다.`;
                    console.log(message);
                    ```
                    
                - Boolean: true와 false
                    - **조건문 또는 반복문에서 boolean이 아닌 데이터 타입은 '자동 형 변환 규칙'에 따라 true 또는 false로 변환됨**
                        
                        
                - null: 변수의 값이 없음을 의도적으로 표현할 때 사용
                - undefined: 변수 선언 이후 직접 값을 할당하지 않으면 자동으로 할당됨
            - 참조 자료형
                - 객체의 주소가 저장되는 자료형(가변, 주소가 복사)
                - Objects(Object, Array, Function)
        - 연산자
            - 할당 연산자
                - 오른쪽에 있는 피연산자의 평가 결과를 왼쪽 피연산자에 할당하는 연산자
                - increment(++) : 피연산자의 값을 1 증가시키는 연산자
                - decrement(--) : 피연산자의 값을 1 감소시키는 연산자
                - += 또는 -=와 같이 더 분명한 표현으로 적는 것을 권장함
            - 비교 연산자
                - 피연산자들(숫자, 문자, Boolean 등)을 비교하고 결괏값을 boolean으로 반환하는 연산자
            - 동등 연산자(==)
                - 두 피연산자가 같은 값으로 평가되는지 비교 후 boolean 값을 반환
                - 비교할 때 암묵적 타입 변환을 통해 타입을 일치시킨 후 같은 값인지 비교
                - 두 피연산자가 모두 객체일 경우 메모리의 같은 객체를 바라보는지 판별
                - 예상치 못한 결과가 발생할 수 있으므로 **특별한 경우를 제외하고 사용하지 않음**
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
                - 조건 표현식의 결괏값을 boolean 타입으로 변환 후 참/거짓을 판단
                
                ```jsx
                const name = 'manager';
                
                if (name === 'admin') {
                  console.log('관리자님 환영합니다.');
                } else if (name === 'manager') {
                  console.log('매니저님 환영합니다.');
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
                		break;
                	case 10:
                		console.log(number);
                		break;
                	default:
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
                  statements
                }
                ```
                
                ```jsx
                const fruits = { a: 'apple', b: 'banana' };
                
                for (const key in fruits) {
                  console.log(key);
                }
                ```
                
            - for...of
                - 반복 가능한 객체(배열, 문자열 등)를 순회할 때 사용
                - 객체의 요소에 대한 반복
                
                ```jsx
                for (variable of iterable) {
                  statements
                }
                ```
                
                ```jsx
                const numbers = [0, 1, 2, 3];
                
                for (const number of numbers) {
                  console.log(number);
                }
                ```
                
    - Functions
        - 모든 JavaScript 함수는 Function 객체
        
        ```jsx
        function name ([param[, param2[, ...paramN]]]) {
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
                
                > **호이스팅이란?
                -** 인터프리터가 변수와 함수의 메모리 공간을 선언 전에 미리 할당하는 것
                - 변수를 정의하는 코드보다 사용하는 코드가 앞서 등장할 수 있다.
                > 
                
                ```jsx
                const funcName = function () {
                	statements
                }
                ```
                
            - 화살표 함수 표현식
                - 함수 표현식의 간결한 표현법
                    - function 키워드 제거 후 매개변수와 중괄포 사이에 화살표(⇒) 작성
                    - 함수의 매개변수가 하나 뿐이라면 매개변수의 () 생략 가능
                        - 인수가 하나도 없을 땐 빈 괄호 또는 _로 표시할 수 있다. 단, 이 때 괄호는 생략할 수 없다.
                    - 함수 본문의 표현식이 한 줄이라면 {}와 return 생략 가능
                        - 본문이 여러 줄로 구성되었다면 중괄호를 사용해야 한다. 단, 이 경우는 반드시 `return` 지시자를 사용해 반환 값을 명기해 주어야 한다.
                
                ```jsx
                function hello() {
                	console.log('Hello!');
                	console.log('World!');
                };
                
                hello();
                ```
                
                ```jsx
                const hello = () => {
                	console.log('Hello!');
                	console.log('World!');
                };
                
                hello();
                ```
                
                ```jsx
                function sum(a, b) {
                	return a + b;
                };
                
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
                
                greeting('홍길동');
                ```
                
                ```jsx
                const greeting = user => console.log(`Hello, ${user}!`);
                
                greeting('홍길동');
                ```