# ⭐ Web - CSS Layout

## 💡 CSS Layout

- 각 요소의 위치와 크기를 조정하여 웹 페이지의 디자인을 결정하는 것
- Display, Position, Float, Flexbox 등

## 💡CSS Position

- Normal Flow에서 요소를 끄집어내서 다른 위치로 배치하는 것
  > Normal Flow : Block 요소(상-하) / Inline 요소(좌-우)
- Position 유형별 특징
  - static
    - 기본값
    - 요소를 Normal Flow에 따라 배치
  - relative
    - 요소를 Normal Flow에 따라 배치
    - 자기 자신을 기준으로 이동
    - 요소가 차지하는 공간은 static일 때와 같음
  - absolute
    - 요소를 Normal Flow에서 제거
    - 가장 가까운 relative 부모 요소를 기준으로 이동
    - 문서에서 요소가 차지하는 공간이 없어짐
  - fixed
    - 요소를 Normal Flow에서 제거
    - 현재 화면 영역(viewpoint)을 기준으로 이동
    - 문서에서 요소가 차지하는 공간이 없어짐
  - sticky
    - 요소를 Normal Flow에 따라 배치
    - 가장 가까운 block 부모 요소를 기준으로 이동
    - 요소가 특정 임계점에 도달했을 때 그 위치에서 고정됨(fixed)
    - 만약 다음 sticky 요소가 나오면 다음 sticky 요소가 이전 sticky 요소의 자리를 대체
      - 이전 sticky 요소가 고정되어 있던 위치와 다음 sticky 요소가 고정되어야 할 위치가 겹치게 되기 때문
- z-index
  - 요소가 겹쳤을 때 어떤 요소 순으로 위에 나타낼지 결정
  - 정숫값을 사용해 Z축 순서를 지정
  - 더 큰 값을 가진 요소가 작은 값의 요소를 덮음

## 💡CSS Float

- 요소를 띄워서 텍스트 및 인라인 요소가 그 주위를 감싸도록 하는 배치
- 왼쪽 혹은 오른쪽으로 띄워 Normal Flow에서 벗어남
- 텍스트 열 내부에 떠다니는 이미지를 포함하면서도 해당 이미지의 좌우에 텍스트를 둘러싸는 간단한 레이아웃을 구현하기 위해 도입
  - 예: 신문 레이아웃

## 💡CSS Flexbox

- 요소를 행과 열 형태로 배치하는 1차원 레이아웃 방식
  - 요소 간 공간 배열과 정렬
- flexbox 기본 사항
  - main axis(주축)
    - flex item들이 배치되는 기본 축
    - main start에서 시작하여 main end 방향으로 배치
  - cross axis(교차 축)
    - main axis에 수직인 축
    - cross start에서 시작하여 cross end 방향으로 배치
  - flex container
    - display: flex; 혹은 display: inline-flex;가 설정된 부모 요소
    - 이 컨테이너의 1차 자식 요소들이 flex item이 됨
    - flexbox 속성값들을 사용하여 자식 요소 flex item들을 배치
  - flex item
    - flex container 내부에 레이아웃 되는 항목
- flex 레이아웃 구성
  - flex container 지정
    - flex item은 행으로 나열
    - flex item은 주축의 시작 선에서 시작
    - flex item은 교차 축의 크기를 채우기 위해 늘어남
  - flex-direction 지정
    - flex item이 나열되는 방향을 지정
    - column으로 지정할 경우 주축이 변경됨
    - -reverse로 지정하면 시작 선과 끝 선이 서로 바뀜
  - flex-wrap
    - flex item 목록이 flex container의 하나의 행에 들어가지 않을 경우 다른 행에 배치할지 여부 설정
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
    - 남는 행 여백을 비율에 따라 각 flex item에 분배
    - flex-grow의 반대는 flex-shrink
      - 넘치는 너비를 분배해서 줄임
  - flex-grow
    - flex item 요소에 flex container 요소 내부에서 할당 가능한 공간을 할당
    - 모든 flex item 요소가 동일한 값을 갖는다면 flex-container 내부에서 동일한 공간을 할당받음
    - 다른 값을 갖는다면 공간 값을 나누어 할당받음
  - flex-basis
    - flex item의 초기 크기 값을 지정
    - flex-basis와 width 값을 동시에 적용한 경우 flex-basis가 우선

## 💡Flexbox 반응형 레이아웃

- flex-wrap을 사용해 반응형 레이아웃 작성
- flex-grow와 flex-basis 활용
