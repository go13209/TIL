# Python

- 파이썬이란?
    - 컴퓨터 프로그래밍 언어 중 하나로 컴퓨터에 하는 명령어의 모음이다.
    - 인터프리터(interpreter) 언어로 소스 코드를 기계어로 변환하는 과정 없이 바로 실행이 가능하다.
    - 파이썬은 객체 지향 언어로 모든 것이 객체로 구현되어 있다.
    

- 객체, 변수, 식별자
    - 객체: 숫자, 문자, 클래스 등 값을 가지고 있는 모든 것
    - 변수: 파이썬 객체를 참조하기 위해 사용하는 이름
        - 할당 연산자(=)를 통해 값을 할당한다.
    - 식별자: 파이썬 객체(변수, 함수, 모듈, 클래스 등)를 식별하기 위해 사용하는 이름
        - 변수의 이름, 상수의 이름, 함수의 이름, 사용자 정의 타입의 이름 등 '이름'을 일반화해서 지칭하는 것이다.
        

- 객체의 종류
    - 숫자
        - 수치형(Numeric Type)
            - 정수(int) : 모든 정수
            - 실수(Float) : 정수가 아닌 모든 실수
            - 복소수(Complex) : 실수부와 허수부로 구성된 복소수
        - 불린형(Boolean Type)
            - True / False : True는 1, False는 0에 해당한다.
            - 비교/논리 연산을 수행함에 있어서 활용된다.
            - 0, 0.0, (), [], {}, "", None ⇒ 모두 False로 변환된다.
        - 연산자(Operator)
            - 산술 연산자: 기본적인 사칙연산 및 수식 계산
                
                
                | + | 덧셈 |
                | --- | --- |
                | - | 뺄셈 |
                | * | 곱셈 |
                | / | 나눗셈 |
                | // | 몫 |
                | % | 나머지 |
                | ** | 거듭제곱 |
            - 복합 연산자: 연산과 할당이 함께 이뤄진다.
                
                
                | a += b | a = a + b |
                | --- | --- |
                | a -= b | a = a - b |
                | a *= b | a = a * b |
                | a /= b | a = a / b |
                | a //= b | a = a // b |
                | a %= b | a = a % b |
                | a **= b | a = a ** b |
            - 비교 연산자: 값을 비교하며 True / False 값을 리턴한다.
                
                
                | < | 미만 |
                | --- | --- |
                | <= | 이하 |
                | > | 초과 |
                | >= | 이상 |
                | == | 같음 |
                | != | 같지 않음 |
                | is | 객체 아이덴티티 |
                | is not | 객체 아이덴티티가 아닌 경우 |
            - 논리 연산자: 논리식을 판단하여 True / False 값을 리턴한다.
                
                
                | and | 모두 참인 경우 참, 그렇지 않으면 거짓 |
                | --- | --- |
                | or | 하나라도 참이라도 참, 그렇지 않으면 거짓 |
                | not | 참, 거짓의 반대의 결과(True를 False로, False를 True로) |
    
    - 시퀀스(Sequence)
        - 시퀀스형 주요 공통 연산자
            
            
            | s[i] | s의 i번째 항목, 0에서 시작한다. |
            | --- | --- |
            | s[i:j] | s의 i에서 j까지의 슬라이스 |
            | s[i:j:k] | s의 i에서 j까지 스텝 k의 슬라이스 |
            | s + t | s와 t 이어 붙이기 |
            | s * n 또는 n * s | s를 그 자신에 n번 더하는 것이다. |
            | x in s | s의 항목 중 하나가 x와 같으면 True, 그렇지 않으면 False |
            | x not in s | s의 항목 중 하나가 x와 같으면 False, 그렇지 않으면 True |
            | len(s) | s의 길이 |
            | min(s) | s의 가장 작은 항목 |
            | max(s) | s의 가장 큰 항목 |
        - 문자열(string): 문자들의 나열
            - 문자열 연산자
                - 인덱싱: 인덱스를 통해 특정 값에 접근할 수 있다.
                - s[1] = 'b’
                    
                    
                    | a | b | c | d | e | f | g | h | i |
                    | --- | --- | --- | --- | --- | --- | --- | --- | --- |
                    | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
                - 슬라이싱: 문자를 잘게 나누는 방법이다.
                - s[2:5] = 'cde’
                    
                    
                    | a | b | c | d | e | f | g | h | i |
                    | --- | --- | --- | --- | --- | --- | --- | --- | --- |
                    | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
                    | -9 | -8 | -7 | -6 | -5 | -4 | -3 | -2 | -1 |
            - 문자열 메서드
                
                
                | .find(찾는 문자) | 특정 문자가 처음으로 나타나는 위치(인덱스)를 반환한다.
                찾는 문자가 없으면 -1을 반환한다. |
                | --- | --- |
                | .index(찾는 문자) | 특정 문자가 처음으로 나타나는 위치(인덱스)를 반환한다.
                찾는 문자가 없다면 오류가 발생한다. |
                | .count(개수를 셀 문자) | 문자열에서 특정 문자가 몇 개인지 반환한다.
                문자뿐만 아니라 문자열의 개수도 확인이 가능하다. |
                | .replace(기존 문자, 새로운 문자) | 문자열에서 기존 문자를 새로운 문자로 수정한 뒤 새로운 문자열을 반환한다.
                특정 문자를 빈 문자열("")로 수정하면 마치 해당 문자를 삭제한 것 같은 효과를 낼 수 있다. |
                | .strip(제거할 문자) | 문자열의 양쪽 끝에 있는 특정 문자를 모두 제거한 새로운 문자열을 반환한다.
                괄호 안에 아무것도 넣지 않으면 자동으로 공백을 제거한다.
                제거할 문자를 여러 개 넣으면 해당하는 모든 문자를 제거한다. |
                | .split(기준 문자) | 문자열을 일정 기준으로 나누어 리스트로 반환한다.
                괄호 안에 아무것도 넣지 않으면 자동으로 공백으로 기준으로 나눈다. |
                | 삽입할 문자.join(iterable) | iterable의 각각 원소 사이에 특정 문자를 삽입한 새로운 문자열을 반환한다.
                문자 간 공백이나 콤마 추가 등 원하는 출력 형태를 위해 사용한다. |
                | .capitalize() | 가장 첫 번째 글자를 대문자로 변경한다. |
                | .upper() | 모두 대문자로 변경한다. |
                | .lower() | 모두 소문자로 변경한다. |
        - 리스트(list): 변경 가능한 값들의 나열
            - 대괄호([]) 혹은 list()를 통해 생성한다.
            - 순서를 가지며 서로 다른 타입의 요소를 가질 수 있다.
            - 순서가 있는 시퀀스로 인덱스를 통해 접근할 수 있다.
            - List Comprehension
                
                **lst = [<expression> for <변수> in <iterable> if <조건식>]**
                
            - 리스트 메서드
                
                
                | .append(x) | 리스트 맨 끝에 새로운 값을 삽입한다. |
                | --- | --- |
                | .extend(iterable) | 리스트에 iterable의 항목을 추가한다. |
                | .insert(i, x) | 정해진 위치 i에 값을 추가한다. |
                | .remove(x) | 리스트에서 값이 x인 것을 삭제한다. |
                | .pop(i) | 특정 인덱스에 있는 원소를 삭제하고 해당 항목을 반환한다.
                i가 지정되지 않으면 마지막 항목을 삭제하고 반환한다. |
                | .clear() | 모든 항목을 삭제한다. |
                | .index(x) | 리스트에서 처음으로 원소가 등장하는 인덱스 값을 반환한다. |
                | .count(x) | 리스트에서 해당 원소의 개수를 반환한다. |
                | .sort() | 리스트를 오름차순으로 정렬한다.
                reverse = True 옵션을 통해 내림차순으로 정렬할 수 있다.
                
                * sorted 함수는 원본 변경 없이 정렬된 리스트를 반환한다. |
                | .reverse() | 리스트 원소들의 순서를 거꾸로 뒤집는다. |
        - 튜플(tuple): 변경 불가능한 값들의 나열
            - 소괄호(()) 혹은 tuple()을 통해 생성한다.
            - 순서를 가지며 서로 다른 타입의 요소를 가질 수 있다.
            - 값에 대한 접근은 리스트와 동일하게 인덱스로 접근할 수 있지만 값 변경은 불가능하며 추가, 삭제도 불가능하다.
        - 레인지(range): 숫자의 나열
            - range(n): 0부터 n-1까지 숫자의 시퀀스
            - range(n, m): n부터 m-1까지 숫자의 시퀀스
            - range(n, m, s): n부터 m-1까지 s만큼 증가시킨 숫자의 시퀀스
    
    - 컬렉션(Collection)
        - 세트(set): 중복 없는 유일한 값들의 모음
            - 중괄호({}) 혹은 set()를 통해 생성한다.
            - 빈 set를 만들기 위해서 set()을 반드시 활용해야 한다.
            - 순서가 없고 중복된 값이 없다.
            - 수학에 집합과 동일한 구조를 가지며 집합 연산도 가능하다.
            - 세트 메서드
                
                
                | .add(x) | 항목 x가 세트에 없다면 추가한다. |
                | --- | --- |
                | .pop() | 세트에서 랜덤하게 항목을 반환하고 해당 항목을 제거한다.
                세트가 비어 있을 경우 KeyError가 발생한다. |
                | .remove(x) | 항목 x를 세트에서 삭제한다.
                항목이 존재하지 않을 경우 KeyError가 발생한다. |
                | .discard(x) | 항목 x가 세트에 있는 경우 항목 x를 세트에서 제거한다. |
        - 딕셔너리(dictionary): 키-값들의 모음
            - 키와 값은 :(colon)으로 구분되고 개별 요소는 ,(comma)로 구분한다.
            - 딕셔너리에 키와 값의 쌍을 추가할 수 있으며 이미 해당하는 키가 있다면 기존 값이 변경된다.
            - 딕셔너리는 기본적으로 key를 순회하며 key를 통해 값을 활용한다.
            - 해시 함수와 해시 테이블을 이용하기 때문에 삽입, 삭제, 수정, 조회 연산의 속도가 리스트보다 빠르다.
            - Dictionary Comprehension
                
                **dict = {key: value for <변수> in <iterable> if <조건식>}**
                
            - 딕셔너리 메서드
                
                
                | .keys() | 딕셔너리의 모든 키를 담은 뷰를 반환한다. |
                | --- | --- |
                | .values() | 딕셔너리의 모든 값을 담은 뷰를 반환한다. |
                | .items() | 딕셔너리의 모든 키-값의 쌍을 담은 뷰를 반환한다. |
                | .get(key[, default]) | 내부에 존재하는 key에 대한 value 값을 반환한다.
                존재하지 않는 key에 대해서는 default 값을 반환한다. |
                | .pop(key[, default]) | 내부에 존재하는 key에 대한 value 값을 삭제하고 반환한다.
                존재하지 않는 key에 대해서는 KeyError가 발생한다.
                두 번째 인자로 default(기본) 값을 지정하여 key가 딕셔너리에 없을 경우 default 값을 반환하고 KeyError를 방지할 수 있다. |
    
    - None: 값이 없음을 표현하기 위한 None 타입
        - 일반적으로 반환 값이 없는 함수에서 사용하기도 한다.
        

- 조건문, 반복문
    - 조건문(Conditional Statement)
        - 참/거짓을 판단할 수 있는 조건식
        - 조건이 참인 경우 들여쓰기 되어 있는 코드 블럭을 실행하고 이외의 경우 else 이후 들여쓰기 되어 있는 코드 블럭 실행한다.
        - else는 선택적으로 활용할 수 있으며 else 조건문을 반드시 적어야 하는 것은 아니다.
        - 복수의 조건식은 elif를 활용하여 표현한다.
        - 조건문은 다른 조건문에 중첩되어 사용할 수 있다.
        
        ```python
        if < expression >:
        		Run this code block
        elif < expression >:
        		Run this code block
        elif < expression >:
        		Run this code block
        else:
        		Run this code block
        		if < expression >:
        				Run this code block
        		else:
        				Run this code block
        ```
        
    - 반복문(Loop Statement)
        - 특정 조건에 도달할 때까지 계속 반복되는 문장이다.
        - 종류
            - while 문
                - 조건식이 참인 경우 반복적으로 코드를 실행한다.
                - 무한 루프를 하지 않도록 종료 조건이 반드시 필요하다.
                
                ```python
                # while 반복문 예제
                # 1부터 사용자가 입력한 양의 정수까지의 총합을 구하는 코드
                
                n = 0
                total = 0
                user_input = int(input())
                
                while n <= user_input:
                		total += n
                		n += 1
                
                print(total)
                ```
                
            - for 문
                - 반복 가능한 객체를 모두 순회하면 종료되며 별도의 종료 조건이 필요하지 않다.
                - 순회 가능한 객체: 컨테이너형(문자열, list, tuple, range, set, dictionary) 등
                
                ```python
                # for 반복문 예제
                # 사용자가 입력한 문자를 한 글자씩 세로로 출력하는 코드
                
                chars = input()
                # 사용자가 'hello'를 입력한 경우
                
                for char in chars:
                		print(char)
                ```
                
            - 반복 제어
                - break: break 문을 만나면 반복문은 종료된다.
                    
                    ```python
                    for i in range(10):
                    		if i > 1:
                    				print('0과 1만 필요해!')
                    				break
                    		print(i)
                    
                    0
                    1
                    0과 1만 필요해!
                    ```
                    
                - continue: continue 이후의 코드 블록은 수행하지 않고 다음 반복을 수행한다.
                    
                    ```python
                    for i in range(6):
                    		if i % 2 == 0:
                    				continue
                    		print(i)
                    
                    1
                    3
                    5
                    ```
                    
                - for-else: 끝까지 반복문을 실행한 이후에 else 문을 실행한다. 단, break를 통해 중간에 종료되는 경우 else 문은 실행되지 않는다.
                    
                    ```python
                    for char in 'apple':
                    		if char == 'b':
                    				print('b!')
                    				break
                    		else:
                    				print('b가 없습니다')
                    
                    b가 없습니다.
                    ```
                    
    

- 파이썬 함수
    - 함수: 특정 기능을 하는 코드의 묶음
        - 특정 명령을 수행하는 코드를 매번 반복하여 작성하지 않고 필요시에만 호출하여 사용할 수 있기 때문에 코드 중복을 방지하고 재사용이 용이하다.
        - 사용자가 직접 함수를 만들어 사용할 수 있다.
    - 사용자 정의 함수
        - 함수 선언은 def 키워드를 통해서 가능하며 함수명()으로 호출한다.
        - 함수는 호출되면 코드를 실행하고 동작 후에 return 값을 반환하며 종료된다. 명시적인 return이 없는 경우에는 None을 반환한다.
    - 함수 인자(Argument)
        - 함수 호출 시 함수의 parameter를 통해 전달되는 값으로 소괄호 안에 할당된다.
        - 위치 인자(positional argument)
            - 기본적으로 함수 호출 시 인자는 위치에 따라 함수 내에 전달된다.
            
            ```python
            def add(x, y):
            		return x + y
            
            add(2, 3)
            ```
            
        - 키워드 인자(keyword arguments)
            - 직접 변수의 이름으로 특정 인자를 전달할 수 있다.
            - 키워드 인자 다음에는 위치 인자를 활용할 수 없다.
            
            ```python
            def add(x, y):
            		return x + y
            
            add(x = 2, y = 5)
            add(2, y = 5)
            ```
            
        - 디폴트 인자 값(default argument value)
            - 기본값을 지정하여 함수 호출 시 인자 값을 설정하지 않아도 되도록 한다.
            - 정의된 것보다 더 적은 개수의 인자들로 호출될 수 있다.
            
            ```python
            def add(x, y = 0):
            		return x + y
            
            add(2)
            ```
            
        - 가변 인자(Variable-length argument)
            - 인자의 개수를 동적으로 받아들이기 위해 사용한다.
            - 몇 개의 위치 인자를 받을지 알 수 없는 함수를 정의할 때 유용하다.
            - 인자들은 **튜플**로 묶여 처리되며 앞에 ***(asterisk)**를 붙여 표현한다.
            
            ```python
            def add(***args**):
            		for arg in args:
            				print(arg)
            
            add(2)
            add(2, 3, 4, 5)
            ```
            
        - 키워드 가변 인자(keyword variable-length argument)
            - 가변 인자와 비슷한 기능을 한다.
            - 몇 개의 키워드 인자를 받을지 알 수 없는 함수를 정의할 때 유용하다.
            - 인자들은 **딕셔너리**로 묶여 처리되며 앞에 ******를 붙여 표현한다.
            
            ```python
            def family(****kwargs**):
            		for key, value in kwargs:
            				print(key, ':', value)
            
            family(father = 'John', mother = 'Jane', me = 'John Jr.')
            ```
            
    - 함수의 범위(Scope)
        - 함수는 함수 내부에 local scope를 생성하며 그 외의 공간은 global scope라고 구분한다.
        - 스코프별 변수의 종류
            - 전역 변수(global variable)
                - global scope에 정의된 변수이다.
                - 함수와 관계 없이 어디서든 접근이 가능하다.
            - 지역 변수(loval variable)
                - 함수 내 local scope에 정의된 변수이다.
                - 선언된 함수 내에서만 접근이 가능하다.
        - 객체 수명주기
            - 객체는 각자의 수명주기(life cycle)가 존재한다.
                - built-in scope: 파이썬이 실행된 이후부터 영원히 유지된다.
                - global scope: 모듈이 호출된 시점 이후 혹은 인터프리터가 끝날 때까지 유지된다.
                - local scope: 함수가 호출될 때 생성되고 함수가 종료될 때까지 유지된다.
                
                ```python
                def func():
                		a = 20
                		print('local', a)
                
                func()
                print('global', a)
                
                # NameError가 발생한다.
                # a는 local scope에서만 존재하기 때문이다.
                ```
                
        - 이름 검색 규칙(Name Resolution)
            - 파이썬에서 사용되는 이름(식별자)들은 이름공간(namespace)에 저장되어 있다.
            - 이름을 찾는 데에는 LEGB Rule이 적용되며 순서는 아래와 같다.
                - Local scope: 정의된 함수
                - Enclosed scope: 특정 함수의 상위 함수
                - Global scope: 함수 밖의 변수, import된 모듈
                - Built-in scope: 파이썬 안에 내장된 함수 또는 속성
            - 즉, 함수 내에서는 바깥 scope의 변수에 접근 가능하나 수정은 할 수 없다.
        - global 문
            - 현재 코드 블록의 전체에 적용되며 나열된 식별자(이름)이 global variable임을 나타낸다.
            - global에 나열된 이름은 같은 코드 블록에서 global 앞에 등장할 수 없다.
            - global에 나열된 이름은 parameter, for 루프 대상, 클래스/함수 정의 등으로 정의되지 않아야 한다.
            
            ```python
            a = 10
            
            def func():
              global a
              a = 3
            
            print(a)
            func()
            print(a)
            
            # 10
            # 3
            # local scope에서 global 변수 값을 변경했다.
            # global 키워드를 사용하지 않으면 local scope에 a 변수가 생성된다.
            ```
            

- 에러/예외, 예외 처리
    - 에러
        - 문법 에러(Syntax Error)
            - 파싱 에러라고도 하며 문법 에러가 발생하면 파이썬 프로그램은 실행되지 않는다.
            - 에러가 감지된 가장 앞의 위치를 가리키는 캐럿(caret) 기호(^)가 표시된다.
        - 예외(Exception)
            - 실행 중에 감지되는 에러로, 문장이나 표현식이 문법적으로 올바르더라도 발생할 수 있다.
            - 실행 도중 예상치 못한 상황을 맞이하면 프로그램 실행을 멈춘다.
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
        - try 문(statement)과 except절(clause)을 이용하여 예외 처리가 가능하다.
        - try 문
            - 오류가 발생할 가능성이 있는 코드를 실행한다.
            - 예외가 발생하지 않으면 except 없이 실행이 종료된다.
        - except 문
            - 예외가 발생하면 except 절이 실행된다.
            - 예외 상황을 처리하는 코드를 받아서 적절한 조치를 취한다.
            

- 파일 입출력, JSON 파일 활용
    - 파일 입출력
        - 파일 입력
            
            **파일 객체 = open(file, mode, encoding=None)**
            
            - file: 파일명
            - mode: 파일 열기 모드
                
                
                | r | 읽기 모드 - 파일을 읽기 위한 옵션 (기본값) |
                | --- | --- |
                | w | 쓰기 모드 - 파일에 내용을 쓸 때 사용하는 옵션
                만약 이미 파일이 존재하면 커서를 맨 앞으로 돌리면서 뒤의 내용을 다 잘라내기 때문에 내용이 사라질 수 있다.
                파일이 존재하지 않는다면 새롭게 파일을 생성한다. |
                | a | 쓰기 모드 - 파일의 마지막에 새로운 내용을 추가할 때 사용하는 옵션
                w 옵션과는 달리 이미 파일이 존재하면 그 파일의 끝에 커서가 존재하고, 그 뒤에 이어쓰기가 가능하다. |
                | x | 파일이 없으면 파일을 생성하고 쓰기 모드로 열린다.
                파일이 존재하면 에러가 발생한다. |
                | b | 바이너리 모드 |
                | t | 텍스트 모드(기본값) |
            - encoding: 인코딩 방식(일반적으로 utf-8 적용)
        - 파일 활용
            - 파일 객체 활용
                
                ```python
                f = open('workfile', 'w')
                
                **f.close()**
                ```
                
                - with 키워드 활용
                
                ```python
                **with** open('workfile') **as** f:
                  read_data = f.read()
                ```
                
            - 파일 입출력과 관련된 처리가 끝나면 close()로 사용한 리소스를 종료해야 한다.
            - with~as 구문을 사용하면 파일 처리 시 close()가 내부적으로 진행되어 명시적으로 close()를 쓰지 않아도 되므로 번거로움을 덜 수 있다.
    
    - JSON 파일 활용
        - JSON은 자바스크립트 객체 표기법으로 개발 환경에서 많이 활용되는 데이터 양식이다.
        - 웹 애플리케이션에서 데이터를 전송할 때 일반적으로 사용한다.
        - 문자 기반(텍스트) 데이터 형식으로 다수의 프로그래밍 환경에서 쉽게 활용할 수 있다.
        - JSON 파일의 활용
            - 객체(리스트, 딕셔너리 등)를 JSON으로 변환
                
                ```python
                import json
                
                d = {"name":"Rilee", "birth":"0320"}
                data = json.dumps(d)
                
                >>> data
                '{"name":"Rilee", "birth":"0320"}'
                ```
                
                - JSON을 객체(리스트, 딕셔너리 등)로 변환
                
                ```json
                {
                    "name": "Rilee",
                    "birth": "0320"
                }
                ```
                
                ```python
                import json
                with open('myinfo.json') as f:
                		json.load(f)
                
                {'name': 'Rilee', 'birth': '0320'}
                ```