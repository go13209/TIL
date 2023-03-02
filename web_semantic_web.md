# ⭐ Web - Semantic Web

## 💡 Semantic Web

- 웹 데이터를 의미론적으로 표현하고 연결하는 개념
- 컴퓨터가 데이터의 내용과 문맥을 더 효율적으로 이해하고 활용할 수 있도록 도움
- 의미론적인 마크업은 검색 엔진이 해당 웹 사이트를 분석하기 쉽게 만들어 검색 순위에 영향을 줌
- 시각 장애 사용자가 스크린 리더기로 웹 페이지를 사용할 때 추가적으로 도움

## 💡 Semantics in HTML

- HTML Semantic 요소
  - 기본적인 모양과 기능 이외에 의미를 가지는 HTML 요소
  - 검색엔진 및 개발자가 웹 페이지의 콘텐츠를 이해하기 쉽게 만들어줌
- 페이지 구조화를 위한 대표적인 semantic 요소
  - header
  - nav
  - main
  - article
  - section
  - aside
  - footer

## 💡 Semantics in CSS

- OOCSS
  - Object-Oriented CSS: 객체 지향적 접근법을 적용하여 CSS를 구성하는 방법론
  - 구조와 외형을 분리
    - 구조: width, height, border, padding, margin, ...
    - 외형: color, border-color, font-color, background-color, ...
  - 컨테이너와 내용을 분리
    - 위치에 의존하지 않는 스타일 정의
    - 어떤 태그라도 동일한 외형 제공
    - 어디에서나 재사용이 가능한 클래스 기반 모듈 구축
- BEM
  - Block Element Modifier: 블록, 요소, 수정자를 사용해 클래스 이름을 구조화하는 방법론
  - 구성
    - Block
      - 문단 전체에 적용된 요소 또는 요소를 담고 있는 컨테이너
      - 재사용 가능한 독립적 블록, 가장 바깥쪽 상위요소
      - 재사용을 위해 margin 또는 padding을 적용하지 않음
    - Element
      - block이 포함하고 있는 한 조각
      - 블록을 구성하는 종속적인 하위요소
    - Modifier
      - block 또는 element의 속성
  - block(전체를 감싸고 있는 블록 요소)\_\_element(내부 요소)--modifier(기능/수정)
- OOCSS, BEM의 의의
  - 재사용 가능한 모듈로 분리함으로써 유지보수성과 확장성을 향상
  - 개발자 간의 협력이 향상되어 공통 언어와 코드 이해를 확립
