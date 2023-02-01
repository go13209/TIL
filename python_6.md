# ⭐ Python - 파일 입출력, JSON 파일 활용, 외부 패키지 활용

## 💡 파일 입출력
- 파일 입력
  - open(file, mode='r', encoding=None)
    - file: 파일명
    - mode: 텍스트 모드
    - encoding: 인코딩 방식(일반적으로 utf-8 활용)
    |Character|Meaninga|
    |'r'|open for reading (default)|
    |'w'|open for writing, truncating the file first|
    |'a'|open for writing, appending to the end of file if it exists|
    |'x'|open for exclusive creation, failing if the file already exists|
    |'b'|binary mode|
    |'t'|text mode (default)|
    |'+'|open for updating (reading and writing)|
- 파일 활용
  - 파일 객체 활용
    ```python
    f = open('workfile', 'w')

    f.close()
    ```
    - with 키워드 활용
    ```python
    with open('workfile') as f:
      read_data = f.read()
    ```
  - with 키워드를 사용하지 않으면 f.close()를 반드시 호출하여 종료시켜야 오류가 발생하지 않음. 따라서 일반적으로 with 키워드를 활용하여 작성

## 💡 JSON 파일 활용
- JSON은 자바스크립트 객체 표기법으로 개발환경에서 많이 활용되는 데이터 양식으로 웹 어플리케이션에서 데이터를 전송할 때 일반적으로 사용함
- 문자 기반(텍스트) 데이터 형식으로 다수의 프로그래밍 환경에서 쉽게 활용 가능함
  - 텍스트를 언어별 데이터 타입으로 변환
  - 언어별 데이터 타입을 적절하게 텍스트로 변환
- JSON 파일의 활용
  - 객체(리스트, 딕셔너리 등)를 JSON으로 변환
    ```python
    import json
    x = [1, 'simple', 'list']
    json.dumps(x)
    '[1, "simple", "list"]'
    ```
    - JSON을 객체(리스트, 딕셔너리 등)로 변환
    ```python
    x = json.load(f)
    ```
- pprint: 임의의 파이썬 데이터 구조를 예쁘게 인쇄할 수 있는 기능을 제공
  ```python
  from pprint import pprint
  with open('data/movie.json', 'r', encoding='UTF8') as f:
    movie = json.load(f)
    pprint(movie)
  ```

## 💡 외부 패키지 활용(requests)
- 요청과 응답
  - **브라우저**를 통해 주소로 요청을 보내고 응답 결과를 브라우저가 웹 화면으로 렌더링함
  - 파이썬을 통해 주소로 요청을 보내고 응답 결과를 파이썬으로 조작함
- API(Application Programming Interface)
  - 컴퓨터나 컴퓨터 프로그램 사이의 연결
  - 일종의 소프트웨어 인터페이스이며 다른 종류의 소프트웨어에 서비스를 제공
  - 사용하는 방법을 기술하는 문서나 표준은 API 사양/명세(specification)
  - API 활용 시 확인 사항
    - 요청하는 방식에 대한 이해
      - 인증 방식
      - URL 생성
        - 기본 주소
        - 원하는 기능에 대한 추가 경로
        - 요청 변수(필수와 선택)
    - 응답 결과에 대한 이해
      - 응답 결과 타입(JSON)
      - 응답 결과 구조