# ⭐ Python - 함수

## 💡 함수
- 특정한 기능을 하는 코드의 조각(묶음)
- 특정 명령을 수행하는 코드를 매번 다시 작성하지 않고 필요시에만 호출하여 간편히 사용 가능(코드 중복 방지, 재사용 용이)
- 구현되어 있는 함수가 없는 경우 사용자가 직접 함수를 작성 가능

## 💡 내장함수
- 파이썬 인터프리터에 내장된 함수로, 별도의 import가 필요하지 않기 때문에 아무런 설정 없이 바로 사용 가능
- 자주 사용하는 함수
  - len(s)
    - 객체의 길이를 반환
    - 인자는 시퀀스 또는 컬렉션일 수 있음
  - sum(iterable, start=0)
    - start 및 iterable의 항목들을 왼쪽에서 오른쪽으로 합하고 합계를 반환
    - iterable의 항목은 일반적으로 숫자며 시작 값은 문자열이 될 수 없음
  - max(iterable)
    - iterable에서 가장 큰 항목이나 두 개 이상의 인자 중 가장 큰 것을 반환
    - 여러 항목이 최댓값이면 함수는 처음 만난 항목을 반환
  - min(iterable)
    - iterable에서 가장 작은 항목이나 두 개 이상의 인자 중 가장 작은 것을 반환
    - 여러 항목이 최솟값 함수는 처음 만난 항목을 반환
- 수학 관련 함수
  - abs(x)
    - 숫자의 절댓값을 반환
    - 인자는 정수, 실수 또는 \_\_abs__()를 구현하는 객체
    - 인자가 복소수면 그 크기를 반환
  - divmod(a, b)
    - 두 수를 받아 몫과 나머지를 반환
  - pow(base, exp, mod=None)
    - base의 exp 거듭제곱을 반환
    - mod가 있는 경우 base의 exp 거듭제곱의 모듈로 mod를 반환
  - round(number, ndigit=None)
    - number를 소수점 다음에 ndigits 정밀도로 반올림한 값을 반환
    - ndigits가 생략되거나 None이면 입력에 가장 가까운 정수를 반환
- 논리 관련 함수
  - all(iterable)
    - iterable의 모든 요소가 참이면 (또는 iterable이 비어있으면) True를 반환
  - any(iterable)
    - iterable의 요소 중 어느 하나라도 참이면 True를 반환
    - iterable이 비어 있으면 False를 반환
- 기타 함수
  - bin(x)
    - 정수를 "0b" 접두사가 붙은 이진 문자열로 반환
  - hex(x)
    - 정수를 "0x" 접두사가 붙은 16진수 문자열로 반환
  - oct(x)
    - 정수를 "0o" 접두사가 붙은 8진수 문자열로 반환
  - ord(c)
    - 유니코드 문자 c에 대응되는 유니코드 숫자로 반환
  - chr(i)
    - 유니코드 숫자가 정수 i에 대응되는 문자를 반환
- map 함수
  - map(function, iterable)
  - 순회 가능한 데이터구조(iterable)의 모든 요소에 함수(function)를 적용하고 그 결과를 map object로 반환
    ```
    numbers = [1, 2, 3]
    result = map(str, numbers)
    print(result, type(result))

    <map object at 0x10e2ca100> <class 'map'>

    list(result)
    # 리스트 형 변환을 통해 결과를 직접 확인
    ```
  - 알고리즘 문제 풀이 시 input 값들을 숫자로 바로 활용하고 싶을 때 사용
    ```
    n, m = map(int, input().split())

    print(n, m)
    print(type(n), type(m))

    3 5
    <class 'int'> <class 'int'>
    ```

## 💡 사용자 정의 함수
- 함수 선언은 def 키워드 활용
- 함수는 함수명()으로 호출
  - parameter가 있는 경우 함수명(값1, 값2, ...)로 호출
  > parameter: 함수를 실행할 때 함수 내부에서 사용되는 식별자  
  Argument: 함수를 호출할 때 넣어주는 값
  ```
  def function(ham): # parameter: ham
    return ham
  
  function('spam') # argument: 'spam'
  ```
- 들여쓰기를 통해 Function body(실행될 코드 블록)를 작성함
- 함수는 parameter를 넘겨줄 수 있음
- 함수는 호출되면 코드를 실행하고 동작 후에 return 값을 반환하며 종료됨
- 반드시 값을 하나만 return
  - 명시적인 return이 없는 경우에는 None을 반환함
  > return: 함수 안에서 값을 반환하기 위해 사용되는 키워드  
  cf. print: 출력을 위해 사용되는 함수

## 💡 Argument
- 함수 호출 시 함수의 parameter를 통해 전달되는 값  
- argument는 소괄호 안에 할당  
  - 필수 argument: 반드시 전달되어야 하는 argument  
  - 선택 argument: 값을 전달하지 않아도 되는 경우는 기본값이 전달
- positional arguments
  - 기본적으로 함수 호출 시 argument는 위치에 따라 함수 내에 전달됨
  ```
  def add(x, y): # add(2, 3)
    return x + y
  ```
- keyword arguments
  - 직접 변수의 이름으로 특정 argument를 전달할 수 있음
  - keyword argument 다음에 positional argument를 활용할 수 없음
  ```
  def add(x, y): # add(x = 2, y = 5) / add(2, y = 5)
    return x + y
  ```
- default arguments values
  - 기본값을 지정하여 함수 호출 시 argument 값을 설정하지 않도록 함
    - 정의된 것보다 더 적은 개수의 argument들로 호출될 수 있음
  ```
  def add(x, y = 0): # add(2)
    return x + y  
  ```
- 정해지지 않은 개수의 arguments
  - 여러 개의 positional argument를 하나의 필수 parameter로 받아서 사용
    - 몇 개의 positional arguments를 받을지 모르는 함수를 정의할 때 유용
  - argument들은 튜플로 묶여 처리되며 parameter에 *를 붙여 표현
  ```
  def add(*args): # add(2) / add(2, 3, 4, 5)
    for arg in args:
    print(arg)
  ```
- 정해지지 않은 개수의 keyword arguments
  - 함수가 임의의 개수 argument를 keyword argument로 호출될 수 있도록 지정
  - argument들은 딕셔너리로 묶여 처리되며 parameter에 **를 붙여 표현
  ```
  def family(**kwargs):
    for key, value in kwargs:
      print(key, ':', value)
  family(father = 'John', mother = 'Jane', me = 'John Jr.')
  ```

## 💡 함수의 범위(Scope)
- 함수는 코드 내부에 local scope를 생성하며 그 외의 공간인 global scope로 구분
- scope
  - global scope: 코드 어디에서든 참조할 수 있는 공간
  - local scope: 함수가 만든 scope. 함수 내부에서만 참조 가능
- variable
  - global variable: global scope에 정의된 변수
  - loval variable: local scope에 정의된 변수
- 객체 수명주기
  - 객체는 각자의 수명주기(life cycle)가 존재
    - built-in scope: 파이썬이 실행된 이후부터 영원히 유지
    - global scope: 모듈이 호출된 시점 이후 혹은 인터프리터가 끝날 때까지 유지
    - local scope: 함수가 호출될 때 생성되고 함수가 종료될 때까지 유지
  ```
  def func():
    a = 20
    print('local', a)
  
  func()
  print('global', a)

  # NameError 발생. a는 local scope에서만 존재하기 때문
  ```
- 이름 검색 규칙(Name Resolution)
  - 파이썬에서 사용되는 이름(식별자)들은 이름공간(namespace)에 저장되어 있음
  - 아래와 같은 순서로 이름을 찾아 나가며 LEGB Rule이라고 부름
    - Local scope: 함수
    - Enclosed scope: 특정 함수의 상위 함수
    - Global scope: 함수 밖의 변수, import 모듈
    - Built-in scope: 파이썬 안에 내장된 함수 또는 속성
  - 즉, 함수 내에서는 바깥 scope의 변수에 접근 가능하나 수정은 할 수 없음
- global 문
  - 현재 코드 블록 전체에 적용되며 나열된 식별자(이름)이 global variable임을 나타냄
    - global에 나열된 이름은 같은 코드 블록에서 global 앞에 등장할 수 없음
    - global에 나열된 이름은 parameter, for 루프 대상, 클래스/함수 정의 등으로 정의되지 않아야 함
  ```
  a = 10
  def func():
    global a
    a = 3

  print(a)
  func()
  print(a)

  # 10
  # 3
  # local scope에서 global 변숫값의 변경
  # global 키워드를 사용하지 않으면 local scope에 a 변수가 생성됨
  ```
