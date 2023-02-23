# ⭐ Web - The box model

## 💡 CSS Box Model

- 모든 HTML 요소를 사각형 박스로 표현
- 박스에 대한 크기, 여백, 테두리 등의 스타일을 지정하는 디자인 개념
- 구성

  - Margin
    - 다른 요소들 사이의 공백
    - 가장 바깥쪽 영역
  - Border
    - 콘텐츠와 패딩을 감싸는 테두리 영역
  - Padding
    - 콘텐츠와 테두리 사이의 공백 영역
  - Content
    - 콘텐츠가 표시되는 영역

- width & height 속성

  - 요소의 너비와 높이를 지정
  - 이때 지정되는 요소의 너비와 높이는 콘텐츠 영역을 대상으로 하므로 사용자가 원했던 박스 너비와 실제 박스의 너비(padding, border 포함)는 다를 수 있음
  - 이 경우 box-sizing 속성을 활용해 요소의 너비와 높이를 계산하는 방법을 지정할 수 있음

    ```html
    <body>
      <div class="box content-box">content-box</div>
      <div class="box border-box">border-box</div>
    </body>
    ```

    ```css
    .box {
      width: 100px;
      border: 2px solid black;
      padding: 10px;
      margin: 20px;
      background-color: lightgray;
    }

    .content-box {
      box-sizing: content-box;
    }
    /* 박스의 너비는 124 (100 + (10*2) + (2*2)) */

    .border-box {
      box-sizing: border-box;
    }
    /* 박스의 너비는 100 */
    ```

- 박스 타입
  - 기본적으로 Block 요소는 상-하, Inline 요소는 좌-우로 배치됨
  - Block
    - 항상 새로운 행으로 나뉨
    - width와 height 속성을 사용하여 너비와 높이를 지정할 수 있음
    - 기본적으로 width 속성을 지정하지 않으면 박스는 inline 방향으로 사용할 수 있는 공간을 모두 차지함(너비를 사용 가능한 공간의 100%로 채우는 것)
    - 대표적인 block 타입 태그
      - h1~6, p, div
  - Inline
    - 새로운 행으로 나뉘지 않음
    - width와 height 속성을 사용할 수 없음
    - 수직 방향
      - padding, margins, borders가 적용되지만 다른 요소를 밀어낼 수는 없음
    - 수평 방향
      - padding, margins, borders가 적용되어 다른 요소를 밀어낼 수 있음
    - 대표적인 inline 타입 태그
      - a, img, span
  - display: inline-block
    - inline과 block 요소 사이의 중간 지점을 제공하는 display 값
    - 요소가 줄 바꿈 되는 것을 원하지 않으면서 너비와 높이를 적용하고 싶은 경우에 사용
    - block 요소의 특징을 가짐
      - 너비 및 높이 속성 적용 가능
      - 패딩, 여백 및 테두리로 인해 다른 요소가 상자에서 밀려남
  - Margin collapsing(마진 상쇄)
    - 두 block 타입 요소의 margin top과 bottom이 만나 큰 margin으로 결합하는 현상
    - 웹 개발자가 레이아웃을 더욱 쉽게 관리할 수 있도록 함
      - 각 요소에 대한 상-하 margin을 각각 설정하지 않고 한 요소에 대해서만 설정할 수 있음
