# ⭐ Web - Bootstrap

## 💡 Bootstrap

- 프론트엔드 라이브러리(Toolkit)
- 반응형 웹 디자인 & CSS 및 JS 기반의 컴포넌트와 스타일 제공
- [Bootstrap 공식 문서](https://getbootstrap.com/)
  - head와 body에 bootstrap **CDN**이 포함된 코드 블록을 가져와 붙여 넣으면 Bootstrap 사용 가능
- 태그의 클래스에 Bootstrap이 정해놓은 이름을 작성하면 Bootstrap 스타일 사용 가능
  - Bootstrap 스타일 및 컴포넌트는 공식 문서 학습을 통해 활용

## 💡 CDN(Content Delivery Network)

- 지리적 제약 없이 빠르고 안전하게 콘텐츠를 전송할 수 있는 전송 기술
- 서버와 사용자 사이의 물리적인 거리를 줄여 콘텐츠 로딩에 소요되는 시간을 최소화(웹 페이지 로드 속도를 높임)

## 💡 Bootstrap Grid system

- 웹 페이지의 레이아웃을 조정하는 데 사용되는 12개의 컬럼으로 구성된 시스템
- 반응형 디자인을 지원해 웹 페이지를 모바일, 태블릿, 데스크톱 등 다양한 기기에서 적절하게 표시할 수 있도록 도움
- 1개의 row 안에 12칸의 column 영역이 구성되며 각 요소는 12칸 중 몇 칸을 차지할 것인지 지정됨
- Offset
  - 일정 크기만큼 그리드 간격을 둘 수 있음
  - 오프셋 선택자를 추가하면 왼쪽으로부터 해당 크기만큼 떨어져서 배치됨
  - 어떤 요소를 중앙 정렬하거나 오른쪽 정렬할 때 유용함
- Gutters
  - Grid system에서 column 사이의 padding 영역
  - gx-\* : 수평 / gy-\* : 수직 / g-\* : 수평 수직
- Breakpoints
  - 웹 페이지를 다양한 화면 크기에서 적절하게 배치하기 위한 분기점
  - 화면 너비에 따라 6개의 분기점 제공(xs, sm, md, lg, xl, xxl)
  - breakpoints마다 설정된 최대 너비 값 "이상으로" 화면이 커지면 grid system 동작이 변경됨
