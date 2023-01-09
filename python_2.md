# ⭐ Python - 조건문, 반복문

## 💡 String Formatting
- 변수를 활용하여 문자열을 만드는 법
  1. \%-formatting
      - %s : 문자열(string)
      - %d : 정수(decimal)
      - %f : 실수(float)
      ```
      name = 'Kim'
      score = 4.5

      print('Hello, %s'% name)
      print('내 성적은 %d' % score)
      print('내 성적은 %f' % score)
        
      # Hello, Kim
      # 내 성적은 4
      # 내 성적은 4.500000
      ```
  2. f-string
      ```
      name = 'Kim'
      score = 4.5
      print(f'Hello, {name}! 성적은 {score}')
      # Hello, Kim! 성적은 4.5

      pi = 3.141592
      print(f'원주율은 {pi:.3}. 반지름이 2일 때 원의 넓이는 {pi*2*2}')
      # '원주율은 3.14. 반지름이 2일 때 원의 넓이는 12.566368'
      ```

## 💡 형 변환(Typecasting): 파이썬에서 데이터 형태는 서로 변환 가능
- 암시적 형 변환(Implicit Typecasting): 사용자가 의도하지 않고 파이썬 내부적으로 자료형을 변환하는 경우
  - bool
  - Numeric type(int, float, complex)
    ```
    True + 3
    # 4
    
    3 + 5.0
    # 8.0
    
    3 + 4j + 5
    # (8+4j)
    ```
- 명시적 형 변환(Explicit Typecasting): 사용자가 특정 함수를 활용하여 의도적으로 자료형으로 변환하는 경우
  - int
    - str(형식에 맞는 문자열만 가능), float -> int
  - float
    - str(형식에 맞는 문자열만 가능), int -> float
  - str
    - int, float, list, tuple, dict -> str
  ```
  # 문자열은 암시적 타입 변환이 되지 않음
  '3' + 4
  TypeError: can only concatenate str (not "int") to str

  # 명시적 타입 변환이 필요함
  int('3') + 4
  # 7

  # 정수 형식이 아닌 경우 타입 변환할 수 없음
  int('3.5') + 5
  ValueError: invalid literal for int() with base 10: '3.5'

  float('3.5') + 5
  # 8.5
  ```

## 💡 제어문(Control Statement)
- 파이썬은 기본적으로 위에서부터 아래로 순차적으로 명령을 수행함
- 특정 상황에 따라 코드를 선택적으로 실행(분기/조건)하거나 계속하여 실행(반복)하는 제어가 필요함
- 제어문은 순서도(flow chart)로 표현 가능
- 종류
  - `조건문(Conditional Statement)`
  - `반복문(Loop Statement)`

## 💡 조건문(Conditional Statement)
- 조건문은 참/거짓을 판단할 수 있는 조건식과 함께 사용
- expression에는 참/거짓에 대한 조건식을 작성
  - 조건이 참인 경우 들여쓰기 되어 있는 코드 블럭 실행
  - 이외의 경우 else 이후 들여쓰기 되어 있는 코드 블럭 실행
    - else는 선택적으로 활용 가능
  ```
  if < expression >:
    Run this code block
  else:
    Run this code block
  ```
  ### 실습 예제
  - 조건문을 통해 변수 num의 값의 홀수/짝수 여부를 출력하시오. 이때 num은 input을 통해 사용자로부터 입력 받으시오.
    ```
    num = int(input())
    if num % 2 == 1:
      print('홀수')
    else:
      print('짝수')
    ```
- 복수 조건문: 복수의 조건식을 활용할 경우 elif를 활용하여 표현
  ```
  if < expressio >:
    Run this code block
  elif < expression >:
    Run this code block
  elif < expression >:
    Run this code block
  else:
    Run this code block
  ```
  ### 실습 예제
  - 미세먼지 농도에 따른 등급이 있을 때, dust 값에 따라 등급을 출력하는 조건식을 작성하시오.
    ```
    dust = 80

    if dust > 150:
      print('매우 나쁨')
    elif dust > 80:
      print('나쁨')
    elif dust > 30:
      print('보통')
    else:
      print('좋음')
    print('미세먼지 확인 완료')
    
    # 조건식을 동시에 검사하는 것이라 아니라 순차적으로 비교하는 것이기 때문에 '150 >= dust > 80' 식으로 적을 필요가 없다.
    ```
- 중첩 조건문: 조건문은 다른 조건문에 중첩되어 사용할 수 있음
  ```
  if < expression >:
    Run this code block
    if < expression >:
      Run this code block
  else:
    Run this code block
  ```
  ### 실습 예제
  - 미세먼지 실습 예제에 중첩 조건문을 활용하여 미세먼지 농도(dust 값)가 300이 넘는 경우 '실외 활동을 자제하세요'라는 메시지를 추가로 출력하고 음수인 경우 '값이 잘못되었습니다'라는 메시지를 출력하시오.
    ```
    dust = -10

    if dust > 150:
      print('매우 나쁨')
      if dust > 300:
        print('실외 활동을 자제하세요')
    elif dust > 80:
      print('나쁨')
    elif dust > 30:
      print('보통')
    else:
      if dust >= 0:
        print('좋음')
      else:
        print('값이 잘못되었습니다')
    ```

## 💡 반복문(Loop Statement)
- 특정 조건에 도달할 때까지 계속 반복되는 일련의 문장
  - 종류
    - `while 문`
      - 종료 조건에 해당하는 코드를 통해 반복문을 종료시켜야 함
    - `for 문`
      - 반복 가능한 객체를 모두 순회하면 종료(별도의 종료 조건이 필요 없음)
    - `반복제어`
      - break, continue, for-else

## 💡 while 문
- while 문은 조건식이 참인 경우 반복적으로 코드를 실행
  - 조건이 참인 경우 들여쓰기 되어 있는 코드 블록이 실행됨
  - 코드 블록이 모두 실행되고 다시 조건식을 검사하며 반복적으로 실행됨
  - while 문은 무한 루프를 하지 않도록 종료 조건이 반드시 필요함
  ```
  while < expression >:
    Run this code block
  ```
  ### 실습 예제
  - 1부터 사용자가 입력한 양의 정수까지의 총합을 구하는 코드를 작성하시오.
    ```
    # 값 초기화
    n = 0
    total = 0
    user_input = int(input())

    while n <= user_input:
      total += n
      n += 1
    print(total)
    ```

## 💡 for 문
- for 문은 시퀀스(string, tuple, list, range)를 포함한 순회 가능한 객체(iterable) 요소를 모두 순회함
  - 처음부터 끝까지 모두 순회하므로 별도의 종료 조건이 필요하지 않음
  - 순회 가능한 객체: 컨테이너형(문자열, 리스트, 튜플, range, set, dictionary) 등
  ```
  for < 변수명 > in < iterable >:
    Run this code block
  ```
  ### 실습 예제
  - 사용자가 입력한 문자를 한 글자씩 세로로 출력하시오.
    ```
    chars = input()
    # 사용자가 'hello'를 입력한 경우

    for char in chars:
      print(char)
    
    h
    e
    l
    l
    o
    ```

## 💡 반복문 제어
- break
  - break 문을 만나면 반복문은 종료됨
  ```
  for i in range(10):
    if i > 1:
      print('0과 1만 필요해!')
      break
    print(i)

    0
    1
    0과 1만 필요해!
  ```
- continue
  - continue 이후의 코드 블록은 수행하지 않고 다음 반복을 수행
  ```
  for i in range(6):
    if i % 2 == 0:
      continue
    print(i)
    
  1
  3
  5
  # continue를 만나면, 이후 코드인 print(i)가 실행되지 않고 바로 다음 반복을 시행
  ```
- for-else
  - 끝까지 반복문을 실행한 이후에 else 문을 실행
    - break를 통해 중간에 종료되는 경우 else 문은 실행되지 않음
  ```
  for char in 'apple':
    if char == 'b':
      print('b!')
      break
  else:
    print('b가 없습니다')

    b가 없습니다.
  ```
  ```
  for char in 'banana':
    if char == 'b':
      print('b!')
      break
  else:
    print('b가 없습니다')

    b!
  ```
