# ⭐ Python - 딕셔너리, 에러/예외, 예외처리

## 💡 딕셔너리(Dictionary)
- 키-값(key-value) 쌍으로 이뤄진 자료구조
  - 키(key): 변경 불가능한 데이터(immutable)만 활용 가능
    - string, integer, float, boolean, tuple, range 가능
    - 리스트, 딕셔너리 등은 불가능
  - 값(value): 모든 값으로 설정 가능
- 키와 값은 :(colon)으로 구분
- 개별 요소는 ,(comma)로 구분
- 변경 가능하며(mutable) 반복 가능함(iterable)
- 딕셔너리에 키와 값의 쌍을 추가할 수 있으며 이미 해당하는 키가 있다면 기존 값이 변경됨
- 키를 삭제하려면 .pop()을 활용하여 삭제하려는 키를 전달
- 키가 없는 경우 KeyError 발생
- 딕셔너리는 기본적으로 key를 순회하며 key를 통해 값을 활용
- 추가 메서드를 활용하여 순회 가능
  - keys(): key로 구성된 결과
  - values(): value로 구성된 결과
  - items(): (key, value)의 튜플로 구성된 결과

## 💡 모듈, 패키지
> 다양한 기능을 하나의 파일로(= 모듈, module) - 다양한 파일을 하나의 폴더로(= 패키지, package) - 다양한 패키지를 하나의 묶음으로(= 라이브러리, library) - 이것을 관리하는 관리자(= 파이썬 패키지 관리자, PIP)
- 모듈
  - 특정 기능을 하는 코드를 파이썬 파일(.py) 단위로 작성한 것
  - 모듈을 사용하기 위해서는 'import 모듈명' 명령어를 사용해 모듈을 불러와야 함
- 패키지
  - 특정 기능과 관련된 여러 모듈의 집합
  - 패키지 안에는 또 다른 서브 패키지를 포함
- PyPI(Python Package Index)에 저장된 외부 패키지들을 설치하도록 도와주는 패키지 관리 시스템

  ### [파이썬 표준 라이브러리(Python Standard Library, PSL)](https://docs.python.org/ko/3/library/index.html)
  - 파이썬에 기본적으로 설치된 모듈과 내장 함수
  - random
    - 숫자/수학 모듈 중 의사 난수 생성(pseudo random number generator)
      - 대표적으로 임의의 숫자 생성, 무작위 요소의 선택, 무작위 비복원 추출(샘플링)을 위한 함수 제공
    - random.randint(a, b)
      - a 이상 b 이하 임의의 정수 N을 반환
    - random.choice(seq)
      - 비어 있지 않은 시퀀스에서 임의의 요소를 반환
      - seq가 비어 있으면 IndexError 발생
    - random.shuffle(seq)
      - 시퀀스를 제자리에서 섞음
    - random.sample(population, k)
      - 무작위 비복원 추출한 결과인 k 길이의 리스트를 반환
  - datetime
    - 날짜와 시간을 조작하는 객체를 제공
    - 사용 가능한 데이터 타입
      - datetime.date, datetime.time, datetime.datetime, datetime.timedelta 등
    - datetime.date(year, month, day)
      - 모든 인자가 필수
      - 인자는 특정 범위에 있는 정수이어야 함
      - 이 범위를 벗어나는 인자가 주어지면 ValueError가 발생
    - datetime.date.today()
      - 현재 지역 날짜를 반환
    - datetime.datetime.today()
      - 현재 지역 datetime.을 반환
      - now()를 활용하면 타임존 설정 가능
  - OS
    - OS(운영체제)를 조작하기 위한 인터페이스 제공
    - os.listdir(path='.')
      - path에 의해 주어진 디렉터리에 있는 항목들의 이름을 담고 있는 리스트 반환
      - 리스트는 임의의 순서로 나열되며 특수 항목은 포함하지 않음
    - os.mkdir(path)
      - path라는 디렉터리를 생성
    - os.chdir(path)
      -path 변경

## 💡 에러, 예외 처리
- 에러
  - 문법 에러(Syntax Error)
    - SyntaxError가 발생하면 파이썬 프로그램은 실행되지 않음
    - 파일 이름, 줄번호, ^ 문자를 통해 파이썬이 코드를 읽어 나갈 때 문제가 발생한 위치를 표현
    - 줄에서 에러가 감지된 가장 앞의 위치를 가리키는 캐럿(caret) 기호(^)를 표시
  - 예외(Exception)
    - 실행 중에 감지되는 에러
    - 실행 도중 예상치 못한 상황을 맞이하면 프로그램 실행을 멈춤
      - 문장이나 표현식이 문법적으로 올바르더라도 발생하는 에러
    - 예외의 여러 종류
      - ZeroDivisionError: 0으로 나누려고 할 때 발생
      - NameError: namespace 상에 이름이 없는 경우
      - TypeError: 타입이 불일치하는 경우
      - ValueError: 타입은 올바르나 값이 적절하지 않거나 없는 경우
      - ModuleNotFoundError: 존재하지 않는 모듈을 import하는 경우
      - ImportError: Module은 있으나 존재하지 않는 클래스/함수를 가져오는 경우
      - IndentationError: Indentation이 적절하지 않은 경우
      - KeyboardInterrupt: 임의로 프로그램을 종료하였을 경우
- 예외 처리
  - try 문(statement)과 except절(clause)을 이용하여 예외 처리 가능
  - try 문
    - 오류가 발생할 가능성이 있는 코드를 실행
    - 예외가 발생하지 않으면 except 없이 실행 종료
  - except 문
    - 예외가 발생하면 except 절이 실행
    - 예외 상황을 처리하는 코드를 받아서 적절한 조치를 취함

## 💡 예외 발생시키기
- raise
  - raise를 통해 예외를 강제로 발생시킴
  - raise <표현식>(메시지)
  - 실제 프로덕션 코드에서 활용
- assert
  - assert를 통해 예외를 강제로 발생시킴
  - assert <표현식>, <메시지>
  - 상태 검증에 사용되며 표현식이 False인 경우 AssertionError
  - 일반적으로 디버깅 용도로 사용
  - 특정 조건이 거짓이면 발생