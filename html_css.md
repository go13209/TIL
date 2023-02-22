# ⭐ HTML / CSS

## 💡 HTML(Hyper Text Markup Language)

- 웹 페이지의 의미와 구조를 정의하는 언어
  - Hypertext
    - 웹 페이지를 다른 페이지로 연결하는 링크
    - 참조를 통해 사용자가 한 문서에서 다른 문서로 즉시 접근할 수 있는 텍스트
  - Markup Language
    - 태그 등을 이용하여 문서와 데이터의 구조를 명시하는 언어
- HTML Element
  - 하나의 요소는 여는 태그와 닫는 태그, 그리고 그 안의 내용으로 구성됨
  - 닫는 태그는 태그 이름 앞에 슬래시가 포함되며 닫는 태그가 없는 태그도 존재
- HTML Attributes
  - 규칙
    - 요소 이름 다음에 바로 오는 속성은 요소 이름과 속성 사이에 공백이 있어야 함
    - 하나 이상의 속성들이 있는 경우엔 속성 사이의 공백으로 구분함
    - 속성값은 여닫는 따옴표로 감싸야 함
  - 목적
    - 나타내고 싶지 않지만 추가적인 기능, 내용을 담고 싶을 때 사용
    - CSS가 해당 요소를 선택하기 위한 값으로 활용됨
  - 속성은 되도록 class만 사용하도록 함
    - 개발 시 id, 요소 선택자 등 여러 선택자와 함께 사용할 경우 우선순위 규칙에 따라 예기치 못한 스타일 규칙이 적용되어 전반적인 유지보수가 어려워질 수 있기 때문
    - 문서에서 단 한 번 유일하게 적용될 스타일의 경우에만 id 선택자 사용을 고려
- 구조
  ```html
  <!DOCTYPE html>
  <html lang="en">
    <head>
      <meta charset="UTF-8" />
      <title>My page</title>
    </head>
    <body>
      <p>This is my page</p>
    </body>
  </html>
  ```
  - \<!DOCTYPE html>
    - 해당 문서가 html로 문서라는 것을 나타냄
  - \<html>\</html>
    - 전체 페이지의 콘텐츠를 포함
  - \<title>\</title>
    - 브라우저 탭 및 즐겨찾기 시 표시되는 제목으로 사용
  - \<head>\</head>
    - HTML 문서에 관련된 설명, 설정 등
    - 사용자에게 보이지 않음
  - \<body>\</body>
    - 페이지에 표시되는 모든 콘텐츠
  - Heading & Paragraphs : h1~6, p
  - Lists : ul, ol, li
    - Unordered : ul
    - Ordered : ol
  - Emphasis & Importance : em, strong

## 💡 CSS(Cascading Style Sheet)

- 웹 페이지의 디자인과 레이아웃을 구성하는 언어
- CSS 적용 방법
  1. 인라인(Inline) 스타일
     ```html
     <!DOCTYPE lang="en">
     <head>
       ...
     </head>
     <body>
       <h1 style="color: blue; background-color: yellow;">Hello World!</h1>
     </body>
     </html>
     ```
     - CSS 인라인 스타일은 사용하지 않는 것을 권장함
       - 문서 유지보수가 힘들어짐
       - CSS와 HTML 구조 정보가 혼합되어 작성되기 때문에 코드를 이해하기 어렵게 만듦
  2. 내부(Internal) 스타일 시트
     ```html
     <!DOCTYPE lang="en">
     <head>
       ...
       <title>Document</title>
       <style>
         h1 {
           color: blue;
           background-color: yellow;
         }
       </style>
     </head>
     <body>
       <h1>Hello World!</h1>
     </body>
     </html>
     ```
  3. 외부(External) 스타일 시트
     ```html
     <!DOCTYPE lang="en">
     <head>
       ...
       <link rel="stylesheet" href="style.css">
       <title>Document</title>
     </head>
     <body>
       <h1>Hello World!</h1>
     </body>
     </html>
     ```
     ```css
     /* style.css */
     h1 {
       color: blue;
       background-color: yellow;
     }
     ```
  - 별도의 CSS 파일 생성 후 불러오기
- CSS Selectors 종류
  - 기본 선택자
    - 전체(\*) 선택자
    - 요소(tag) 선택자
      - 지정한 모든 태그를 선택
    - 클래스(class) 선택자
      - 주어진 클래스 속성을 가진 모든 요소를 선택
      - 예: .index는 class="index"를 가진 모든 요소를 선택
    - 아이디(id) 선택자
      - 주어진 아이디 속성을 가진 요소 선택
      - 문서에는 주어진 아이디를 가진 요소가 하나만 있어야 함
      - 예: #index는 id="index"를 가진 요소를 선택
    - 속성(attribute) 선택자
  - 결합자(Combinators)
    - 자손 결합자(" "(space))
      - 첫 번째 요소의 자손 요소들 선택
      - 예: p span은 \<P> 안에 있는 모든 \<span>을 선택(하위 레벨 상관 없이)
    - 자식 결합자(>)
      - 첫 번째 요소의 직계 자식만 선택
      - 예: ul > li은 \<ul> 안에 있는 모든 \<li>를 선택(한 단계 아래 자식들만)
- Cascade(계단식) & Specificity(우선순위)
  - 동일한 요소에 적용할 수 있는 같은 스타일을 두 가지 이상 작성했을 때 어떤 규칙이 이기는지 결정하는 것
  - Cascade(계단식)
    - 동일한 우선순위를 같은 규칙이 적용될 때 CSS에서 마지막에 나오는 규칙이 사용
  - Specificity(우선순위)
    - 선택자별로 정해진 우선순위 점수에 따라 점수가 높은 규칙이 사용
    - 우선순위 순서
      1. !important
         - Cascade의 구조를 무시고 모든 우선순위 점수 계산을 무효로 하는 가장 높은 우선순위
         - 꼭 필요한 경우가 아니면 사용하지 않는 것을 권장함
      2. 우선순위
         - 인라인 스타일 > id 선택자 > class 선택자 > 요소 선택자
      3. 소스 코드 순서
- 상속
  - 기본적으로 CSS는 상속을 통해 부모 요소의 속성을 자식에게 상속함
  - 이를 이용해 코드의 재사용성을 높임
  - 상속되는 속성: Text 관련 요소(font, color, text-align), opacity, visibility 등
  - 상속되지 않는 속성: Box model 관련 요소(width, height, margin, padding, border, box-sizing, display), position 관련 요소(position, top/right/bottom/left, z-index) 등
