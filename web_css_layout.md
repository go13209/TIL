# ⭐ Web - Positioning for CSS Layout

## 💡 CSS Layout

- 각 요소의 위치와 크기를 조정하여 웹 페이지의 디자인을 결정하는 것
- Display, Position, Floats, Flexbox 등

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
